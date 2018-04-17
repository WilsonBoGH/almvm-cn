---
title: Version Controlling with Git using Team Foundation Server
layout: page
sidebar: tfs
permalink: /labs/tfs/git/
folder: /labs/tfs/git/
---

Lab version:15.4

Last updated:11/15/2017

## 概述

在本实验中，您将了解Team Foundation Server 2018和Visual Studio 2017中的Git源代码管理工具. Git是一个分布式版本管理系统，其中存储库既可以在本地（例如在开发人员的计算机上）存在，也可以存储在Team Foundation Server上。TFS Git支持GFS虚拟文件系统 ([GVFS](http://www.gvfs.io/)) ，GFS几乎可以使您可以无限扩展Git存储库。微软的Windows团队使用它来管理超过300万个，共300GB的文件。

# 关于Fabrikam Fiber的项目背景

这套动手实验室使用一家虚拟的公司Fabrikam Fiber作为您正在了解的场景的背景。Fabrikam Fiber向美国提供有线电视和相关服务。他们正在迅速增长，并且已经拥抱Windows Azure部署他们的网站，并允许用户在网站上自助购票。他们还使用ASP.NET MVC应用程序为其客户经理管理客户订单。

在这套动手实验室中，您将参与许多涉及Fabrikam Fiber开发和测试团队的场景。这个由8-10人组成的团队决定使用Visual Studio应用程序生命周期管理工具来管理他们的源代码，运行他们的生成，测试他们的网站，并计划和跟踪项目。

## 练习1：开始使用Git

在本练习中，您将学习如何创建，克隆和推送Git存储库中的提交到Team Foundation Server。

### 任务1：创建一个Git仓库

1. 使用用户 **Sachin Raj (VSALM\Sachin)**登录。所有的用户密码都是 **P2ssw0rd**。

1. 从任务栏启动**Visual Studio 2017**并打开**Team Explorer**。您现在应该连接到**FabrikamFiber**团队项目。如果您没有自动连接到**FabrikamFiber**项目，请单击管理连接，然后双击**FabrikamFiber**项目来执行此操作。

    ![](images/000.png)

1. There are a few reasons why Fabrikam Fiber might want to use Git as their source control option within Team Foundation Server. One reason could be that they are collaborating with developers using a tool such as Xcode, which supports the Git protocol natively. Another reason could be that they have developers working offline (such as during a commute) who want to commit code locally when they are offline and check this code into Team Foundation Server when they get into the office. Microsoft now offers teams the ability to utilize Git without sacrificing the integrated application lifecycle management capabilities offered by Team Foundation Server. Visual Studio 2017 also provides developers with a great experience for working with any Git repository - whether it's hosted by Team Foundation Server, a local repository, or another Git provider.
Fabrikam Fiber希望在Team Foundation Server中使用Git作为其源代码管理的原因有几个。其中一个原因是开发人员使用Xcode等工具进行开发，Xcode本身支持Git。另一个原因是开发人员需要在脱机状态下工作，并且希望在脱机状态下在本地提交代码，并在进入办公室时将此代码复制到Team Foundation Server中。微软现在为团队提供了Git源代码管理支持。Visual Studio 2017还为开发人员提供了管理Git存储库的工具 - 无论存储库是由Team Foundation Server，本地存储库还是其他Git工具创建的。

1. 从**Home**下拉菜单中选择**Projects and My Teams \| New Team Project**。

    ![](images/001.png)

1. 将新项目命名为**"FabrikamCommunity"**，然后单击**Next**。

    ![](images/002.png)

1. 选择**Scrum**流程模板，然后单击**Next**继续。

    ![](images/003.png)

1. 选择**Git**作为版本管理，然后单击 **Finish**。

    ![](images/004.png)

1. 在创建新的Git团队项目之后，单击**Close**返回到Visual Studio。

### 任务2：克隆Git存储库

1. 在**Team Explorer**中，单击**Clone this repository**。

    ![](images/005.png)

1. 使用默认路径和存储库位置，然后单击**Clone**。

    ![](images/006.png)

1. 单击**Manage Connections**按钮，然后双击**FabrikamCommunity**以连接到新建的团队项目。

    ![](images/007.png)

### 任务3：提交代码并链接到工作项目

1. 在**Team Explorer**中，单击**Home**按钮，然后单击**Settings**。

    ![](images/008.png)

1. 点击**Git**下的**Global Settings**。

    ![](images/009.png)

1. 输入Sachin Raj的电子邮件地址（**sachin@vsalm.local**），然后点击**Update**。

    ![](images/010.png)

1. 单击**Team Explorer**中的**Home**按钮。

    ![](images/011.png)

1. 在浏览器中连接到TFS网站，并选择**FabrikamCommunity**团队项目，从主菜单选择**Team \| New Work Item \| Product Backlog Item**打开**New Product Backlog Item**表单。

1. 输入**"Create new web site"**标题，然后点击**Save**按钮。工作项目保存后，请记下ID。

    ![](images/012.png)

1. 回到Visual Studio。在**Team Explorer**中，单击**Solutions**下方的**New...**。

    ![](images/013.png)

1. 在**New Project**窗口中，选择**Visual C# \| Web \| ASP.NET Web Application**序模板并单击**OK**。

    ![](images/014.png)

1. 选择**MVC**模板，然后单击**OK**。

    ![](images/015.png)

1. 项目创建后，在**Team Explorer**中单击**Changes**查看文件提交的列表。

    ![](images/016.png)

1. 滚动到**included changes**列表的最后，.gitattributes和.gitignore文件被自动添加到项目中。**.gitattributes**文件包含Git设置，以控制GIT中的操作。而**.gitignore**文件指定忽略修改的文件。

    ![](images/017.png)

1. 如果您想排除特定文件（或基于扩展名的文件类型），可以在此处右键单击它并选择其中一个选项。这会为你更新**.gitignore**。现在不要做这个操作。

    ![](images/018.png)

1. 输入提交注释，注释以类似于**"initial MVC site for work item #247"**。输入**"#"**后紧跟工作项ID，将在提交到TFS服务器时自动将此次提交链接到ID对应的工作项。这里使用您保存的产品待办事项ID替换这里的247。

    ![](images/019.png)

1. 通过单击**Commit All**来提交更改。

    ![](images/020.png)

1. 让我们对网站进行一些小改动。在**Solution Explorer**中，从**Views\Shared**文件夹中打开**_Layout.cshtml**。

    ![](images/021.png)

1. 将页面标题**"My ASP.NET Application"**的末尾修改为**"Community"**（大约在第**6**行）。

    ![](images/022.png)

1. 在**Team Explorer**中，输入提交注释，然后单击**Commit All**。弹出提示时选择**Save**保存对文件的更改。

    ![](images/023.png)

### 任务4：向服务器同步提交

1. 通过单击**Sync**导航到提交视图。

    ![](images/024.png)

1. **Team Explorer**中的**Synchronization**视图显示传入和传出的提交。但是，由于此项目尚未发布到源代码管理，因此您只需单击**push**即可。

    ![](images/025.png)

    ![](images/026.png)

1. 最后，让我们快速在TFS网站中浏览一下这些提交。在**Team Explorer**中，单击**Web Portal**。

    ![](images/027.png)

1. 从Web门户的**Code**下拉列表中选择**Commits**。

    ![](images/028.png)

1. 点击第一个（底部）提交。

    ![](images/029.png)

1. 请注意，一个工作项目已根据注释中的ID标记链接到这个提交。点击展开它，然后选择**"Create new web site"**工作项以在新选项卡中查看它。

    ![](images/030.png)

1. 查看后关闭工作项目选项卡。

1. 点击Sachin的名字，然后点击 **Pushed on**链接。

    ![](images/031.png)

1. 您可以通过单击其中一个链接来浏览或下载此特定提交的版本。

    ![](images/032.png)

### 任务5：标记发布

1. 虽然看起来不多，但产品团队已经决定该版本的网站正是v1.0所需要的。为了标记它，请导航到**Tags**选项卡，然后单击**Create Tag**。

    ![](images/033.png)

1. 在**name**中输入**"v1.0"**，**Description**中输入**"First release!"**，点击**Create**。

    ![](images/034.png)

1. 您现在已经在此版本上标记了该项目。您可以出于各种原因对提交进行标记，并且TFS可以灵活地编辑和删除它们，也可以管理标记的权限。

    ![](images/035.png)

## 练习2：Git分叉，分支和合并

In this exercise, you will learn about Git forking, branching, and merging support in Visual Studio. In general, forking and branching are often used to help switch development contexts and to isolate risk. For example, a core project team might use Git forks to allow people from outside the team to contribute to the project without allowing them direct commit access. Since a Git fork is a server-side copy of the project, the experience is the same, except that it provides a layer of manageability for the owner. Git branching is a similar concept that allows someone to work within a project without committing to the master branch. For teams of 2-5, it is recommended that you use only branches (and not forks) for most scenarios. Creating a Git branch is a lightweight (and therefore fast) operation, as you are simply creating a new reference to an existing commit. This is very different from a Git fork or Team Foundation Version Control (TFVC) branching where the entire source tree needs to be duplicated server-side. We will also take a quick look at the merging support for Git projects.
在本练习中，您将学习有关Visual Studio中的Git分叉，分支和合并等功能。通常，分叉和分支常常用于切换开发环境，实现隔离并行开发的风险。例如，核心项目团队可能会使用Git分支来允许团队外的人员为项目提供修改，而不允许他们直接提交修改。由于Git fork是项目的服务器端副本，所以体验是相同的，只不过它为所有者提供了一层可管理性。Git分支是一个类似的概念，允许成员在一个项目中工作而不允许直接在主分支提交修改。建议您在大多数情况下只使用分支（而不是分支）。创建一个Git分支是一个轻量，快速的操作，因为您只是创建对现有提交的新引用。这与Git分叉或TFVC分支非常不同，因为Git分叉或TFVC的分支需要在服务器端复制整个存储库。我们还将快速了解对Git合并的支持。

### 任务1：分叉存储库

1. 从导航栏中，单击**Fork**。该分叉将用于团队外的人员为项目提供更改。例如，如果有人想提交对Bug的修改，他们会将其推送到此分叉上的分支并请求拉取。团队中的成员（这里是Sachin）会评审拉取请求，在满足合并要求后通过合并将变更合并到主项目中

    ![](images/036.png)

1. 将**Repository name**设置为**"FabrikamCommunity.External.fork"**并单击**Fork**。请注意，您可以指定包含所有分支，但通常只分叉**default branch**。

    ![](images/037.png)

1. 在Visual Studio中单击**Clone**。将分叉的存储库克隆到本地。

    ![](images/038.png)

1. 单击**Allow**以允许Visual Studio读取克隆文件。

    ![](images/039.png)

1. 点击 **Clone**克隆存储库。

    ![](images/040.png)

1. 克隆完成后，在**Solution Explorer**中找到**WebApplication1.sln**，然后双击将其打开。请注意，尽管它与之前Git存储库几乎完全相同，但它是与之前存储库关联的完全不同的存储库。

    ![](images/041.png)

### 任务2：分支代码

1. 在**Team Explorer**中，单击 **Branches**.

    ![](images/042.png)

1. 假设我们想创建一个新的分支来在网站上进行一些开发工作。右键单击**master**分支节点并选择**New Local Branch From**。

    ![](images/043.png)

1. 将名称设置为**"users/sachin/about"**，然后单击**Create Branch**。请注意，该名称使用的分支命名将此分支创建在**"users/sachin"**下。

    ![](images/044.png)

1. 双击**about**签出分支。

    ![](images/045.png)

1. 在**Solution Explorer**中, 从**Controllers**文件夹中打开**HomeController.cs**文件。

    ![](images/046.png)

1. 按照如以下屏幕截图所示修改**About**方法。

    ![](images/047.png)

1. 右键单击编辑器空白处并选择**Source Control \| Commit**。

    ![](images/048.png)

1. 在**Team Explorer**中，输入提交注释"**Sachin version**"，然后单击**Commit All**。出现提示时选择保存更改。

    ![](images/049.png)

1. 此时，这些更改已提交到本地存储库。导航到**Branches**视图。

    ![](images/050.png)

1. 双击**Master**分支，此时**HomeController.cs**文件的原始版本显示在代码编辑器窗口中。

    ![](images/051.png)

    ![](images/052.png)

1. 如果您想继续在本地工作，则不必将分支推送到服务器。正如您在前面的练习中看到的那样，您可以继续在本地工作并向新分支提交其他修改。在**Team Explorer**中，右键单击**about**分支并选择**View History**。

    ![](images/053.png)

    ![](images/054.png)

1. 现在您可以将其合并回主分支并删除此分支，或将其推送到服务器端的存储库，以便其他团队成员可以拉取你的提交。现在通过右键单击**about**分支并选择**Push Branch**选项来发布分支。

    ![](images/055.png)

1. 打开**Remote Desktop**连接到VSALM。使用用户**Clemri Steyn (VSALM\Clemri)**进行连接。所有的用户密码都是P2ssw0rd。

1. 从任务栏启动**Internet Explorer**。

1. 从项目集合下拉列表中选择**FabrikamFiberCollection**。

    ![](images/056.png)

1. 将鼠标悬停在**FabrikamCommunity**团队项目上并选择**Code**。

    ![](images/057.png)

1. 从**FabrikamCommunity**存储库下拉菜单中选择**FabrikamCommunity.External.fork**。

    ![](images/058.png)

1. 单击**Clone**按钮并按照之前的工作流程在Visual Studio中克隆该项目。

    ![](images/059.png)

1. 在**Solution Explorer**中，双击**WebApplication1.sln**解决方案将其打开。

    ![](images/060.png)

1. 修改Sachin修改的相同**HomeController.cs**文件，但是这次将文本改为不同的内容。通常Clemri会像Sachin一样在分支中进行此项更改，但为了实验目的，这里将直接在**master**分支提交修改。

    ![](images/061.png)

1. 和之前一样，在代码编辑器的空白处右键单击并选择**Source Control \| Commit**。

1. 在**Team Explorer**中，提交注释输入"**Clemri version**"，然后单击**Commit All**。提示时选择保存更改。请注意，Clemri在**master**分支直接提交了修改。

    ![](images/062.png)

1. 从提交反馈中单击**Sync**。

    ![](images/063.png)

1. 点击**Sync**以执行同步。 

    ![](images/064.png)

1. 通过最小化远程桌面会话，返回用户Sachin的操作界面。

### 任务3：合并存储库中的更改

1. 从Sachin的角度来看，他迄今已经创建了一个基于**master**的本地分支，并在此分支提交了修改，然后发布了该分支。现在他想继续将**about**分支上的修改合并到**master**分支。

1. 在**Team Explorer**中，双击签出**master**分支。

    ![](images/065.png)

1. 展开**Merge**选项。

    ![](images/066.png)

1. 选择**about**分支作为源并单击**Merge**。

    ![](images/067.png)

1. 请注意，**master**分支当前处于签出状态，并且**HomeController.cs**显示为**about**版本。合并是在本地通过更新**master**分支指向，将其指向为**about**分支的最新提交。

    ![](images/068.png)

1. 右键单击 **Team Explorer** 的**master**分支，然后选择**View History...**选项。

    ![](images/069.png)

1. 历史视图现在展示了当前代码是如何通过相关的各个分支的提交生成的。

    ![](images/070.png)

1. Still unaware of Clemri's change pushed directly to the **master** branch earlier, Sachin will now attempt to push his commit. Navigate to the **Sync** view in **Team Explorer** via the navigation dropdown.

    ![](images/071.png)

1. Click **Sync** to attempt a pull and a push with the server.

    ![](images/072.png)

    > **Note:** If you see a popup notifying that an open file has been changed externally, click **Yes** as this is expected.

1. Visual Studio reports that we can't push our commit yet due to a conflict. Click **Resolve the conflicts**.

    ![](images/073.png)

1. In the **Resolve Conflicts** view, select **HomeController.cs** from the **Conflicts** section and click **Merge**.

    ![](images/074.png)

1. The **Merge** window used for Git conflict resolution is very similar to the one used with Team Foundation Version Control. Go ahead and assume that Sachin's change is correct, so check the box shown in the top right pane.

    ![](images/075.png)

1. Click **Accept Merge**.

    ![](images/076.png)

1. Click **Commit Merge**.

    ![](images/077.png)

1. In the **Changes** view, note that conflicts have been resolved but the changes still need to be committed. Enter a message and then click the **Commit All** dropdown and select **Commit All and Sync**.

    ![](images/078.png)

1. Navigate to the **Home** view in **Team Explorer** and click **Web Portal**.

    ![](images/079.png)

1. Select the **Code \| Commits** from the navigation.

    ![](images/080.png)

1. Here we can see a full list of our commits so far, along with a handy visualization of the branches and commits.

    ![](images/081.png)

1. Select the **Branches** tab to view all branches published to the repository.

    ![](images/082.png)

### Task 4: Managing repo security and permissions

1. Now let's take a quick peek at managing security and permissions for Git repositories hosted in Team Foundation Server. From the **Repositories** dropdown select **Manage Repositories**.

    ![](images/083.png)

1. The first thing to note is that you can easily create additional Git repositories within the same team project.

    ![](images/084.png)

1. Select the **FabrikamCommunity.External.fork** repository node. You can manage repository level security here for your users and security groups.

    ![](images/085.png)

1. Select the **Master** branch node. Security level settings that affect only the currently selected branch can be made here, providing fine-grained control for your repository if needed.

    ![](images/086.png)

### Task 5: Managing branch policies

1. When you want people on your team to review code in a Git team project, you can use a pull request to review and merge the code. Pull requests enable developers working in topic branches to get feedback on their changes from other developers prior to submitting the code into the master branch. Any developer participating in the review can see the code changes, leave comments in the code, and give a "thumbs up" approval if they're satisfied with those changes.

1. Although it is possible to utilize pull requests without any further configuration, let's take a quick look at how to setup branch policies. Select the **Branch Policies** tab.

    ![](images/087.png)

1. Since there could be issues from anyone committing directly to the **master** branch (like Clemri did earlier), Sachin has decided to put some policies in place to prevent certain problems. Check **Protect this branch** to get started.

    ![](images/088.png)

1. Check the option to **Require a minimum number of reviewers** and set the minimum number of reviewers to **"1"**. Also check **Allow users to approve their own changes** (to keep things simple in this lab).

    ![](images/089.png)

    > **Note:** It is also possible to configure branch policy such that a build is triggered whenever updates are made to the master branch. You can even have the merge fail when the build fails. This is useful for teams looking to adopt continuous integration.

1. There are also options to check or (or even require) work item linking, comment resolution, and specific merge strategies.

    ![](images/090.png)

1. You can make use of branch policies that effectively put in a gate that helps prevent inadvertent or low quality commits by automatically initiating a build, or by requiring code reviews by certain individuals. For example, you can use **Build validation** to block pull requests if the pull request changes don't build.

    ![](images/091.png)

1. It is also possible to require specific reviewers for specific portions of your code base. For example, let's say that Sachin now needs to sign off on all changes made to the ASP.NET MVC controllers. Click **Add automatic reviewers**.

    ![](images/092.png)

1. Add **Sachin** as a **Reviewer** and set **Paths** to cover everything in the **Controllers** folder at **"/WebApplication1/WebApplication1/Controllers/*"**. Click **Save**.

    ![](images/093.png)

1. Click **Save Changes** to update the master branch policies. Close the administration browser tab.

    ![](images/094.png)

### Task 6: Reviewing code and merging using pull requests

1. Switch back to the **Clemri** RDP session.

1. Click **Sync** to ensure that the local copy of **master** matches what's on the server. If you have **HomeController.cs** open in the editor, you may be prompted to reload it. It will reflect Sachin's merged changes.

    ![](images/095.png)

1. Now let's say that Clemri is working on the project and needs to update some of the controller code. To do this, he will first create a topic branch based on **master**. Navigate to **Branches** in **Team Explorer**. Right-click the **master** branch and select **New Local Branch From**...

    ![](images/096.png)

1. For the branch name, use something like **"users/clemri/controllerupdate".** Use the default option to **Checkout branch**. Click **Create Branch**.

    ![](images/097.png)

1. As before, the new branch will appear using the folder structure you specified. This can make dealing with many branches much easier, especially when using multiple levels of categorization.

    ![](images/098.png)

1. Locate the **users/sachin/about** branch under **remotes/origin**. Although we know that these changes were already merged into the local **master** branch we're working with, it would be very easy to pick specific commits from another branch to pull into the code here. Right-click the **about** branch to expose some additional branch management options. Note that you have the option to **cherry-pick** commits to apply to the current branch (but don't do it now). Press **Esc** to dismiss the context menu.

    ![](images/099.png)

1. Update the **About** method from **HomeController.cs** with the new message **"Clemri's enhanced description page."**

    ![](images/100.png)

1. In **Team Explorer**, provide a commit message and then click **Commit All**. Save the changes when prompted.

    ![](images/101.png)

1. In the **Branches** view of **Team Explorer**, right-click the topic branch and select **Push Branch**.

    ![](images/102.png)

1. After successfully publishing the branch, click **Create a pull request**. This will open the pull request on the portal via your browser.

    ![](images/103.png)

1. Make sure the **FabrikamCommunity.External.fork** branch is selected and click **Create** to create a pull request with the default options. Note that you could optionally add additional users to review or associate work items if desired.

    ![](images/104.png)

1. After the pull request is created, the pull request view shows what merge is proposed, the provided description, and a set of tabs listing associated files and commits. You can also see the required policies and reviewers.

    ![](images/105.png)

1. To demonstrate the branch policy in action, let's say Clemri attempts to complete the pull request by himself. Select **Set auto-complete \| Complete**.

    ![](images/106.png)

1. Despite the reminder about policy violations, click **Complete merge** anyway to see what happens.

    ![](images/107.png)

1. As expected, Clemri is notified that the request first needs to be approved by at least one reviewer first.

    ![](images/108.png)

1. Click **Approve**, followed by **Complete**, and then **Complete Merge** in the dialog.

    ![](images/109.png)

1. Note that although we've fulfilled the reviewer quantity, we didn't fulfill the requirement for **Sachin** to approve any changes to the controllers.

    ![](images/110.png)

1. At this point in the workflow, **Sachin** needs to be notified of this pull request through some communication channel, whether that is in person, through Skype, through team room notification, or via TFS pull request alert. For the purposes of this short exercise, however, we will just skip to Sachin checking pull requests for this project.

1. Switch users back to **Sachin** by minimizing the RDP window.

1. In the web portal, navigate to **Code \| Pull Requests**.

    ![](images/111.png)

1. Select the link provided on the pull request from Clemri.

    ![](images/112.png)

1. Sachin can now review all of the files and commits associated with the pull request and make a decision. It is also possible for Sachin to have a conversation with Clemri (and perhaps other reviewers) in order to help make the decision, or perhaps even request additional work be performed before the pull request will be approved.

1. Let's assume that Sachin is ready to approve the request as-is. There are a couple ways to do this. Click **Set auto-complete**.

    ![](images/113.png)

1. The automatic completion feature enables you to approve pull request for automatic completion before all policies have been applied. For example, if a successful build is required before the PR can be completed, this step enables that to happen automatically after all policies have succeeded. You can also specify whether to delete the branch after merging and/or if you want to **squash changes**. Selecting the option to squash changes will merge all commits from the target branch into a single commit in order to help keep things a little tidier.

    ![](images/114.png)

1. In this case, we won't use automatic completion, so click **Cancel**.

    ![](images/115.png)

1. Before approving, provide some positive feedback to **Clemri**, such as **"This looks **good**. Way to go @<VSALM\Clemri> :-)"** and click **Comment**. Note that you can use markdown and emojis, as well as @ reference other users. You can also use # references for work items, such as "#47". As you type, there is a live preview below so that you can see exactly what will show up.

    ![](images/116.png)

1. Select **Approve \| Approve**.

    ![](images/117.png)

1. Now that all policies have been fulfilled, click **Complete** and **Complete merge** to finish the process.

    ![](images/118.png)

1. Switch users back to **Clemri** by bringing up the RDP window.

1. Thanks to live updates, the pull request should already show the comment and that it was approved.

    ![](images/119.png)
