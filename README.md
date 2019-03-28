# Welcome to Azure Immersion Day 2019!

The aim of this all-day workshop is to familiarize you with the Microsoft Azure public cloud and some of its core components. Y'all (yes, I'm Southern :-)) have taken a survey asking which technologies are most relevant to you. I've taken some time to prepare a few hands-on labs.   

By the time you leave the workshop, you should know the following:
- How to navigate Azure and how to spin up new resources to explore Azure
- Know how to analyze spend and govern resource costs
- Understand Azure database options including SQL, MySQL, PostgreSQL, MariaDB and others in Azure
- Have a fundamental understanding of Azure Storage and Backup
- How to create and administer a serverless website
- Understand how to secure resources and how security in the cloud relates to the security practices already implemented on-campus

## Pre-Reqs
- Signup for a [free GitHub account](https://github.com/) if you don't have one already
- Install [the free Visual Studio Code editor](https://code.visualstudio.com/Download). This is the most (marketing would have to back me up here :-)) lightweight Integrated Development Environment (IDE).
  - [After VS Code install, Install Azure Pipelines extension](https://marketplace.visualstudio.com/items?itemName=ms-azure-devops.azure-pipelines)
  - [GitHub Pull Requests extension for VS Code extensions](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)
- Ensure you can access https://portal.azure.com with your intitutional (xyz@abc.edu) logins.
- [Download Free Git Desktop](https://desktop.github.com/)



# Immersion Day Agenda

### Session 1: Introduction to Azure and Azure Fundamentals 

- **0900-1000:** This session gives a quick overview of Azure, Azure Cloud Shell, Azure Storage, Compute and Networking. You'll also understand how we will be interacting with the different technologies of the presented in the day. NOTE: I will try to limit my Azure 101 overview to 30 min and then we can run through a simple lab.
  
  - [Exercise 1 Azure Active Directory Security](AAD/AAD.md)

### Session 2: Serverless Website as a Service in Azure
- **1000-1100:** We're going to walk through website creation and management of the [App Service - Web Apps](https://docs.microsoft.com/en-us/azure/app-service/overview) platform in Azure! 
  
  - [Exercise 2: *Microsoft Learn* App Service Creation](https://docs.microsoft.com/en-us/learn/modules/host-a-web-app-with-azure-app-service)
    - **Note** that MS Learn says to get started with a "sandbox." This is not needed as you already have a resource group from exercise 1 that is your very own in which you can do all the tasks in the Exercise.
    - **Note** Make sure to use your own resource group from Exercise 1

### Session 3: Azure SQL Database as a Service
- **1115-1215:** We'll focus on Azure's fully managed Platform-as-a-Service (PaaS) [SQL solution](https://docs.microsoft.com/en-us/azure/sql-database/)

  - [Exercise 3: *Microsoft Learn* provisioning of a SQL database](https://docs.microsoft.com/en-us/learn/modules/provision-azure-sql-db/)
    - **Note** that MS Learn says to get started with a "sandbox." This is not needed as you already have a resource group from exercise 1 that is your very own in which you can do all the tasks in the Exercise.
    - **Note** Make sure to use your own resource group from Exercise 1
  
### Session 4: Azure Cloud Storage and Backup
- **1330-1430:** This session will cover Azure storage, backup and DR functionality available. Azure was the first cloud to focus on hybrid (on-premises + cloud-native) technologies so this sessions will undoubtedly leave questions. Please [follow-up here for backup](https://docs.microsoft.com/en-us/azure/backup/backup-overview) and [follow-up here for BCDR tech aka ASR - Azure Site Recovery.](https://docs.microsoft.com/en-us/azure/site-recovery/)
  
  -  [Exercise 4: Setup Azure Backup to backup your local PC](backup/tutorial-backup-windows-server-to-azure.md)


### Session 5: Azure DevOps (Pipelines for CI/CD)
- **1445-1600:** Azure DevOps is a HUGE suite of products that include [Boards](https://docs.microsoft.com/en-us/azure/devops/boards/index) (Kanban), [Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/index) (CI/CD Automation), [Artifacts](https://docs.microsoft.com/en-us/azure/devops/artifacts/index?view=azure-devops) (Package Manager), [Test Plans](https://docs.microsoft.com/en-us/azure/devops/test/index-tp?view=azure-devops), and [Repos](https://docs.microsoft.com/en-us/azure/devops/repos/index?view=azure-devops) (Source code repository Manager)

  - [Exercise 5: Using CI/CD Pipelines in Azure](devops-project/exercise5.md)


# Follow-Up
Thanks for spending time with Microsoft today. We're ALWAYS thrilled to come and speak about our technology and we'd love to hear back from you! Please see below for our contact information and survey.
# Immersion Day Survey
## **[Immersion Day Survey](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3vmVKFttl1JjVF3shHsVeNUQVVQMVhBMTlINVUzUjU5U1gwWlo5MlNYTS4u)**
# Microsoft Contact
## Joey Brakefield, Cloud Solutions Architect (Southeast Region -- Atlanta, GA)
- Email:    joey.brakefield@microsoft.com 
- Twitter:  http://twitter.com/kfprugger
- LinkedIn: https://www.linkedin.com/in/joeybrakefield/ 
- GitHub:   https://github.com/kfprugger

## Tim Wheatley, Account Technology Strategist (Southeast Region -- Atlanta, GA)
- Email:    tim.wheat@microsoft.com
- Twitter:  @wheatleyt
- LinkedIn: https://www.linkedin.com/in/timwheatley/


# Key Links
## Alpharetta Microsoft Technology Center 
- [Take a look at the upcoming free Microsoft-tech events!](https://events.microsoft.com/?timeperiod=next90Days&isSharedInLocalViewMode=true&country=United%20States&language=English&city=Atlanta,%20Georgia,%20United%20States)

## Internships and Free Azure Links
- [Azure Free $200 credit](https://azure.microsoft.com/en-us/offers/ms-azr-0044p/)
- [Azure Internships and Programs](https://careers.microsoft.com/us/en/ur-lp-united-states)

## [Learning Links](https://github.com/kfprugger/MLDay/blob/master/Training.md#training-links-for-azure)
- [Azure Learning Paths](https://docs.microsoft.com/en-us/learn/browse/?products=azure%2Cvs-code)
- [Microsoft Docs - Full Documentation and Tutorials for Each Azure Service](https://docs.microsoft.com/en-us/azure/#pivot=products&panel=all)
- [Free Pluralsight Learning Provided by Microsoft](https://www.pluralsight.com/partners/microsoft/azure?aid=7010a000001xDURAA2)
- [Cloud Architecture and API Overview in Azure](https://channel9.msdn.com/shows/Azure-Friday/Learning-Azure-Part-2-Architecture-and-interactive-APIs-for-NET-and-REST-APIs?ocid=AID754288&wt.mc_id=CFID0314)
- [GitHub Quickstart Templates to Test Out New Tech!](https://github.com/Azure/azure-quickstart-templates)
- [Azure Governance Links - For IT Admins in Azure](https://www.linkedin.com/feed/update/urn:li:activity:6488065944924094464/)

## [How to Price Azure?](https://azure.microsoft.com/en-us/pricing/calculator/?msclkid=f7ddc7cbfbb91f535bb19b8084682384&OCID=AID719825_SEM_YI7Ea97y&lnkd=Bing_Azure_Brand&dclid=CInq6rjwieACFdBgwQodZYYAxw)
