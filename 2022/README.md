# UPM Dynamic Template Starter Kit

The purpose of this dynamic template starter kit is to provide the data structure and development guidelines for new dynamic templates meant for **Unity**.

We hope you enjoy your experience. You can use **#devs-templates** on Slack to provide feedback or ask questions regarding your dynamic template development efforts.

> **Note:** Unity Standards were introduced at the start of 2021.1 with sets of standards for packages. With 2021.2, Unity Standards now include [standards for dynamic templates](https://github.cds.internal.unity3d.com/unity/standards/blob/2021.2/sets/USS-0009.md). Compliance with these standards is **mandatory** before you can release a new template. For more information, see the Scholar course [Working with Unity Standards](https://scholar.internal.unity3d.com/course/working-with-unity-standards).

## Are you ready to add a dynamic template?
The Dynamic Templates are a work-in-progress for the Unity Package Manager and, in that sense, there are a few criteria that must be met for your template to be considered on the template list at this time:
- **Your code accesses public Unity C# APIs only.** If you have a native code component, it will need to ship with an official editor release. Internal API access might eventually be possible for Unity made packages, but not at this time.
- **Your code doesn't require security, obfuscation, or conditional access control.**  Anyone should be able to download your dynamic template and access the source code.
- **You are willing to bleed with us a little!** Dynamic templates creation and editing as well as Packman is still in development, and therefore has a few rough edges that will require patience and workarounds.

## Share your plans (Register)

Dynamic templates will be available to our user through the Hub, and organized by categories _(2d, 3d, xv, ...)_. In that sense, the purpose, name, category, and content of your template should first be discussed with the Production Management team, so that this information can be properly curated to match Unity's strategy.  Please contact **@trevor.yeung** on _slack_ to start this conversation.

This will help inform Product, Project, Release and Documentation Teams to coordinate between dependencies. It also allows shared awareness for the whole organization.
We then can also track it in our directory listing.

## Dynamic template Development Structure

The dynamic template is a project itself, so it should be very straightforward to develop with.

```none
<Project Root>
 │
 ├── README.md
 ├── Assets
 │       ├─ Scenes
 │       │     └── SampleScene.unity
 │       └─ Tests
 │            ├── Editor
 │                     └── EditorExampleTest.cs
 │            └── Runtime
 │                      ├── RuntimeTests.asmdef
 │                      └── RuntimeExampleTest.cs
 ├── ProjectSettings
 └── Packages
         ├─ manifest.json
         └─ com.unity.template.mytemplate
                   ├── package.json
                   ├── CHANGELOG
                   ├── LICENSE
                   ├── Documentation~
                   ├── README.md
                   ├── Third Party Notices.md
                   └── QAReport.md
```

## Develop your dynamic template

The dynamic template is a Unity Editor project itself, as such, it should be very straightforward to develop with. Here's how to set it up:

1. ##### Clone the `Template Starter Kit` repository locally

	In a console (or terminal) application, choose a place to clone the repository and perform the following :
	```git clone git@github.cds.internal.unity3d.com:unity/com.unity.template-starter-kit.git```

1. ##### Create a new repository for your package and clone to your desktop

	On Github.cds create a new repository with the name of your package (Example: "com.unity.template.platformer")
	In a console (or terminal) application, choose a place to clone the repository and perform the following :
	```git clone git@github.cds.internal.unity3d.com:unity/com.unity.template.[your-package-name]```

1. ##### Copy the contents of the `Template Starter Kit` folder to your new package. 
    Be careful not to copy the Template Starter Kit `.git` folder over.

1. ##### Rename the template package

    Rename the folder `Package/com.unity.template.mytemplate` by replacing `mytemplate` with your own dynamic template's name.
    This will be the package used to define your dynamic template when publishing and should match the name of your repository on github.cds.

    You may be wondering why we include `com.unity.template.mytemplate` in the project's packages. This package will describe your dynamic template to our users, and will be the package when publishing your template. It will not be included in projects our users create from your template, but will be referenced so users can access template information such as documentation or license information.

1. ##### Fill in your dynamic template's package information

	Update the following required fields in `Packages/com.unity.template.mytemplate/package.json`:
	- `name`: Dynamic template's package name, it should follow this naming convention: `com.unity.template.[your-template-name]`
    (Example: `com.unity.template.3d`)
	- `displayName`: Package user friendly display name. (Example: `First person shooter`). <br>__Note:__ Use a display name that will help users understand what your dynamic template is intended for.
	- `version`: Package version `X.Y.Z`, your project **must** adhere to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).
	- `unity`: Minimum Unity Version your dynamic template is compatible with. (Example: `2018.3`)
	- `unityRelease`: Optional, specify a patch release your package is compatible with (Example: `0a8`)
	- `description`: This is the description for your template which will be displayed to the user to let them know what this template is for. This description shouldn't include anything version-specific and should stay pretty consistent across template versions.
	- `dependencies`: Specify the dependencies the template requires. If you add a package to your project, you should also add it here. We try to keep this list as lean as possible to avoid conflicts as much as possible.

1. ##### Update **README.md**

    The README.md file should contain all pertinent information for template developers, such as:
	* Prerequisites
	* External tools or development libraries
	* Required installed Software

    `Note`: The Readme file at the root of the project should be the same as the one found in the template package folder. 

1. ##### Prepare your documentation

    Rename and update `Packages/com.unity.template.mytemplate/Documentation~/your-package-name.md` documentation file.

    Use this documentation template to create preliminary, high-level documentation for the _development_ of your template's package. This document is meant to introduce other developers to the features and sample files included in your dynamic template.

    Your template's documentation will be made available online and in the editor during publishing to guide our users.

1. ##### Update the changelog   

    Update the changelog at `Packages/com.unity.template.mytemplate/CHANGELOG.md`

	Every new feature or bug fix should have a trace in this file. For more details on the chosen changelog format, see [Keep a Changelog](http://keepachangelog.com/en/1.0.0/).

	Changelogs will be made available online to inform users about the changes they can expect when downloading a dynamic template. As a consequence, the changelog content should be customer friendly and present clear, meaningful information.

1. ##### Open your cloned project and develop!

    Start **Unity**, open your template project folder. Once opened, you can modify the project settings, the project assets and even the packages dependencies to suit your needs. Your dynamic template will contain all the content of your project.

## Create an Experimental version

Initial versions of templates **can** go through an experimental phase to gather feedback from users. Experimental indicates to users that this is a work in progress and it is expected to change in the future. Once the template has been in use for a while by users, and vetted by Unity's Release QA team, its `exp` tag can then be removed, and the template can join the ranks of official Unity templates.

**Experimental**  -  ex: `"version" : "0.1.0"` or `"version": "1.2.0-exp"`

Expectations of an experimental template:
- Expected Package structure respected
- Template loads in Unity Editor without errors
- License file present in template package folder - With third party notices file if necessary

## Make sure your dynamic template meets all legal requirements

All templates are *required* to COMPLETE AND SUBMIT [THIS FORM](https://docs.google.com/forms/d/e/1FAIpQLSe3H6PARLPIkWVjdB_zMvuIuIVtrqNiGlEt1yshkMCmCMirvA/viewform) to receive approval. It is a simple, streamlined form that tells legal if there are any potential issues that need to be addressed prior to publication.

##### Update **Third Party Notices.md**

1. If your template includes third-party elements and its licenses are approved, then all the licenses must be added to the `Third Party Notices.md` file in the template package folder. Simply duplicate the `Component Name/License Type/Provide License Details` section if you have more then one licenses.

    a. Concerning `[Provide License Details]` in the `Third Party Notices.md`, a URL can work as long as it actually points to the reproduced license and the copyright information _(if applicable)_.

1. If your package does not have third party elements, you can remove the `Third Party Notices.md` file from your template package folder.

## Adding tests to your template

Tests you add to your template package will be automatically run in Yamato through CI to ensure your template continues to work as expected as the editor's codebase evolves, it is therefore important to invest in a good set of test

You can add tests for your template in the project's `Assets/Tests` folder as you would any normal Unity project. It is advisable to also test your template's integrity so that frequent developers use doesn't change desirable static properties.

You can manually run the tests in the Unity test runner.

## Template CI
Yamato job definitions can be found [here](https://github.cds.internal.unity3d.com/unity/upm-ci-yamato-templates).

There are 3 yml files & jobs that are required to publish a template to candidates:
 - template-pack.yml
 - template-test.yml
 - template-publish.yml

Unique to templates, `template-pack.yml` contains a pre-pack job called "Primed Artifacts". If configured correctly, this job will lauch the template in the specified editor version, and ensure the generated artifacts (`Library/Artifacts/**`, `Library/ArtifactDB`, `Library/SourceAssetDB`) are passed into the pack job. Ensure the `-projectPath` and artifact paths point to the template's root directory.

CI will test your template on every commit on `Yamato`.   
This will validate that the template package as well as embedded packages (if any) have the right structure, have tests and do not create console logs when opened with Unity.   
The CI will also automatically test the template as it would be used by a user on multiple editor versions and OS.  
You might need to tweak the list of editors and OS you want to test the template on. For more information, please [go here](https://confluence.hq.unity3d.com/pages/viewpage.action?spaceKey=PAK&title=Setting+up+your+package+CI)

`Note`: To make use of the CI, your repository must be added to Yamato.  
Log in to [Yamato](https://yamato.cds.internal.unity3d.com/) and click on the Project + button on the top right.  This will open a dialog asking for you to specify a git url and project name.

## Trying out your template locally.

If you want to test your template locally from a user's perspective, you will need to make it available to a Unity Editor. This can be accomplished by following these steps:

1. Use upm-ci tools to test your template

	[How to Install UPM-CI](https://github.cds.internal.unity3d.com/unity/upm-ci-utils/blob/dev/README.md#installation)
	
	1. **To run all your template tests** 
	    1. Open a console (or terminal) window and cd your way inside your template project folder

	        ```upm-ci template test -u 2020.3``` 

	        You can test against many versions of Unity with the -u parameter: 
 
	        - Testing on a specific version: use `-u 2019.1.0a13`
	        - Testing on a latest release of a version: use `-u 2019.1`
	        - Testing on the latest available trunk build: use `-u trunk`
	        - Testing on a specific branch: use `-u team-name/my-branch`
	        - Testing on a specific revision: use `-u 3de2277bb0e6`
	        - Testing with an editor installed on your machine: use `-u /absolute/path/to/the/folder/containing/Unity.app/or/Unity.exe`
	
	        By default, this will download the desired version of the editor in a .Editor folder created in the current working directory.

	1. **To test what a user would see**
	    1. Open a console (or terminal) window and cd your way inside your template project folder

	        ```upm-ci template pack``` 
	        This will generate a folder /upm-ci~/templates/ containing a .tgz file of your converted template.

	    1. Include the tarballed template package in Unity editor

    	    You can then copy the template's `tgz` package file in Unity in one of these paths to make it available in the editor when creating new projects:

    	    1. Mac: `<Unity Editor Root>/Contents/Resources/PackageManager/ProjectTemplates`

		    1. Windows: `<Unity Editor Root>/Data/Resources/PackageManager/ProjectTemplates`

	    1. Preview your dynamic template

    	    Open Unity Hub. Locate the editor to which you added your template to.
	        When creating a new project, you should see your template in the templates list:

            ![Template in new project](Packages/com.unity.template.mytemplate/Documentation~/images/template_in_new_project.png)

            Note: f you are launching the Unity editor without the hub, you will not see additional templates in the list.

## Publishing your template for use in the Editor

The first step to get your package published to production for public consumption is to send it to the candidates repository, where it can be evaluated by QA and Release Management.  You can publish your template to the candidates repository through the added CI, which is the **recommended** approach.

1. Once you are ready to publish a new version, say version `1.0.0`, you can add a git tag `rc-1.0.0` to the commit you want to publish. The CI will validate and then publish your template to `candidates`.

1. Request that your template package be published to production by [filling out the following form](https://docs.google.com/forms/d/e/1FAIpQLSeEOeWszG7F5mx_VEYm8SrjcIajxa5WoLXh-yhLvw8odsEnaQ/viewform)

1. Once your template is published to production, the last step is to create the Ono PR to include your template with a Unity Release, and have it be discovered in the Hub. To do so, create a branch that includes your template in `External/PackageManager/Editor/editor_installer.json`

`Note`: You can retrieve a version of your template package as an artifact from CI pipelines following any commit made to your repository.  This will allow you to easily test a change at any point during your development.

## USS-0009: Dynamic template standards

Set of standards for dynamic templates available on the Unity Hub.

### Standards control

- Verification set owner: Trevor Yeung
- Applicable for: All types of dynamic template: blank, learning (microgame), and sample templates

#### Summary of standards in USS-0009

The tables below summarize standards contained in this verification set. For details on how to validate against these standards, see [Verification checklist](VerificationChecklist.md).

| Category                                                     | Mandatory standards                                          | Recommended standards                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Dynamic Templates Foundation](../categories/dynamicTemplatesFoundation.md) | [US-0187](../definitions/US-0187/US-0187.md), [US-0188](../definitions/US-0188/US-0188.md), [US-0190](../definitions/US-0190/US-0190.md), [US-0191](../definitions/US-0191/US-0191.md), [US-0192](../definitions/US-0192/US-0192.md), [US-0193](../definitions/US-0193/US-0193.md), [US-0200](../definitions/US-0200/US-0200.md) | [US-0189](../definitions/US-0189/US-0189.md)                 |
| [Editor Usage](../categories/editorUsage.md)                 |                                                              | [US-0195](../definitions/US-0195/US-0195.md), [US-0196](../definitions/US-0196/US-0196.md), [US-0197](../definitions/US-0197/US-0197.md), [US-0198](../definitions/US-0198/US-0198.md), [US-0199](../definitions/US-0199/US-0199.md) |
| [Assets Foundation](../categories/assetsFoundation.md)       | [US-0061](../definitions/US-0061/US-0061.md), [US-0063](../definitions/US-0063/US-0063.md) | [US-0057](../definitions/US-0057/US-0057.md)                 |
| [Packages Foundation](../categories/packagesFoundation.md)   | [US-0005](../definitions/US-0005/US-0005.md), [US-0006](../definitions/US-0006/US-0006.md), [US-0007](../definitions/US-0007/US-0007.md), [US-0017](../definitions/US-0017/US-0017.md), [US-0023](../definitions/US-0023/US-0023.md) |                                                              |
| [Data Collection](../categories/dataCollection.md)           | [US-0037](../definitions/US-0037/US-0037.md)                 |                                                              |
| [Documentation](../categories/documentation.md)              | [US-0040](../definitions/US-0040/US-0040.md)                 |                                                              |
| [Documentation for Packages](../categories/documentationForPackages.md) | [US-0039](../definitions/US-0039/US-0039.md)                 |                                                              |
| [Legal and Licensing](../categories/legalAndLicensing.md)    | [US-0032](../definitions/US-0032/US-0032.md), [US-0033](../definitions/US-0033/US-0033.md) |                                                              |
| [Platforms & Partners](../categories/platformsAndPartners.md)                        | [US-0026](../definitions/US-0026/US-0026.md), [US-0028](../definitions/US-0028/US-0028.md) |                                                              |
| [Quality](../categories/quality.md)                          | [US-0016](../definitions/US-0016/US-0016.md), [US-0029](../definitions/US-0029/US-0029.md) |                                                              |
| [Quality for Packages](../categories/qualityForPackages.md)  | [US-0019](../definitions/US-0019/US-0019.md)                 |                                                              |

**#unity-standards**


Version 1.0.4


## FAQ

#### Can I inherit another package template?

You cannot inherit from another package template. You can however use another package template as a starting point to create a new one.

