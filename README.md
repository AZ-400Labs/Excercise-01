# Excercise-01

Exercise 1: Introduction to Azure DevOps Build
In this exercise, you will create a basic build pipeline from a template, track and review the new build job, and trigger a continuous integration build.

Task 1: Creating a basic build pipeline from a template
In this task, you will create and configure a build pipeline by using a predefined template.

1. In the web browser displaying your Azure DevOps organization with the Enabling Continuous Integration with Azure Pipelines project you generated in the previous exercise, in the vertical navigational pane, select the Pipelines section and ensure that the Pipelines view is displayed.

   Note: Alternatively, you can access the project page directly by navigating to the [https://dev.azure.com/your-Azure-DevOps-account-name/Enabling%20Continuous%20Integration%20with%20Azure%20Pipelines) URL, where the your-Azure-DevOps-account-name placeholder, represents your account name.

2. On the Pipelines pane, hover the mouse pointer over the entry representing the existing PartsUnlimitedE2E pipeline to reveal the ellipsis symbol on the right side.

3. Click the ellipsis and, in the dropdown menu, click Edit.

   Note: In order to avoid two pipelines being triggered later in the lab, start by disabling the CI trigger for the pipeline created by the template.

4. On the Tasks tab of the PartsUnlimitedE2E pane, click the Triggers tab, clear the checkbox Enable continuous integration, click Save & queue and then click Save.

5. To create a new pipeline, navigate back to the Pipelines view by selecting Pipelines in the vertical navigational pane in the Azure DevOps portal.

6. Back on the Pipelines pane, click New pipeline to create a new build pipeline.

   Note: The default option for build pipelines involves the use of YAML. For this lab, you will use the classic editor.

7. On the Where is your code>? pane, click the Use the classic editor link at the bottom of the page.

   Note: You need to start by configuring the source repository. Every major platform is available, but the default options are all we need here. This build will use the master branch of the PartsUnlimited repo.

8. Ensure that the Azure Repos Git option with the PartsUnlimited repository and master branch entries are selected, and click Continue.

9. On the Choose a template pane, in the Search text box, type ASP.NET, in the list of results, select the ASP.NET template and click Apply to apply this template to the build definition.

   Note: Note that there are many options that should cover all of our mainstream scenarios. For our purposes here, we'll just build the project using the baseline ASP.NET template. The process for this build pipeline is easy to follow. After getting the source, Azure DevOps will use NuGet to restore any dependent packages. Then, the project will be built and tested. The results will then be published to the configured target.

10. On the Tasks tab, look for test Assemblies task , right-click and disable selected task(s).

11. Select the Variables tab and review its content.

    Note: Here you can configure special parameters to be used during the build, such as the configuration or platform.

12. Select the Triggers tab and check the Enable continuous integration checkbox.

    Note: This automatically invokes the build whenever source changes are committed. Triggers allow you to automatically invoke builds on a schedule, when another build completes, or when changes are made to the source.

13. Select the Options tab and review its content.

    Note: This section includes a wide variety of options related to the build workflow. Note that you'll generally configure options for specific build tasks on the configuration views of the tasks themselves.

14. Select the History tab.

    Note: At this point, the tab does not contain any entries, but it will show a history of changes you make to the build definition.

15. Select the Save & Queue tab header and, in the dropdown menu, select Save & Queue entry to save and queue a new build.

    Note: You can define the retention time for pipeline artifacts from Project Settings > Settings > Retention policy. These settings enable you to configure which pipeline runs are retained and for how long.

16. In the Run pipeline pane, accept the default options and click Save and run. This will automatically display the Summary tab of the pipeline run job, with the Queued status.


Task 2: Tracking and reviewing a build
In this task, you will track and review the new build job.

    Note: Once the build begins, you'll be able to track the console output per task.

1. On the Summary tab of the pipeline run job, in the Jobs section, click Agent job 1. This will display the details pane of the job.

    Note: If you want to review an earlier task, you can scroll the right pane to review its logs.

2. Once the build completes successfully, on the job details pane, click the left-facing arrow to return to the summary view.

    Note: The summary view provides overview details about the build, including details about commits, tests, and artifacts.



Task 3: Invoking a continuous integration build
In this task, you will trigger a continuous integration build.

[!KNOWLEDGE] Note: In the first task of this exercise, you configured the build to support continuous integration. In this task, you will test its functionality.

1. In the web browser window displaying your project settings in the Azure DevOps portal, in the vertical navigational pane, select the Repos section and ensure that the Files view is displayed.

2. In the middle pane, navigate to the file PartsUnlimited-aspnet45/src/PartsUnlimitedWebsite/Views/Home/Index.cshtml and select it.

3. On the Index.cshtml pane, click Edit.

4. On the Index.cshtml pane, make a minor update by changing the line  
        ViewBag.Title = "Home Page"; to ViewBag.Title = "Lab Project Home Page"; and click Commit.

5. On the Commit pane, accept the default commit details and click Commit.

    Note: This will automatically trigger a build.

6. In the vertical navigational pane, select the Pipelines section and ensure that the Pipelines view is displayed.

7. On the Pipelines pane, verify that it contains the entry representing a new build (note that its number contains the trailing .2) which was triggered by your change.

8. Click the build entry to display its details and verify that it completed successfully.


Congratulations!
You have successfully completed this lab
