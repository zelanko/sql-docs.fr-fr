---
title: "Leçon 2 : Spécification des informations de connexion (Reporting Services) | Documents Microsoft"
ms.custom: 
ms.date: 05/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 53
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Active
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4d0667dec1b59d5560ca24176634dddc5d6d8d18
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Leçon 2 : Spécification des informations de connexion (Reporting Services)
Après avoir ajouté un [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] paginé rapport à votre projet de didacticiel dans la leçon 1, maintenant vous devez définir un *source de données*, c'est-à-dire les informations de connexion que le rapport utilise pour accéder aux données à partir d’une base de données relationnelle, base de données multidimensionnelle ou une autre source.  
  
Dans cette leçon, vous utilisez la [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] base de données comme source de données. Ce didacticiel suppose que cette base de données se trouve dans une instance par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] installé sur votre ordinateur local.  
  
### <a name="to-set-up-a-connection"></a>Pour configurer une connexion  
  
1.  Dans le volet **Données du rapport** , cliquez sur **Nouveau** , puis sur **Data Source**.  
Si le volet **Données du rapport** n’est pas visible, cliquez sur **Données du rapport** dans le menu **Affichage**.  

    ![SSRS-table-Tutorial-2-New-Data-source](../reporting-services/media/ssrs-table-tutorial-2-new-data-source.png)
  
   2.  Dans le champ **Nom**, tapez *AdventureWorks2014*.  
  
3.  Vérifiez que l’option **Connexion incorporée** est sélectionnée.  
  
4.  Dans **Type**, sélectionnez **Microsoft SQL Server**.  
  
5.  Dans **Chaîne de connexion**, tapez ce qui suit :  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
     Cette chaîne de connexion part du principe que [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], le serveur de rapports et la base de données [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] sont tous installés sur l’ordinateur local et que vous êtes autorisé à ouvrir une session sur la base de données [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] . Si votre base de données AdventureWorks2014 n’est pas sur l’ordinateur local, modifiez la chaîne de connexion et remplacez *localhost* avec le nom de votre instance de serveur de base de données.
  
     >[!NOTE]  
    >Si vous utilisez [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services ou une instance nommée, la chaîne de connexion doit comporter des informations sur l'instance :  
    >  
    >`Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
    >  
    >Pour plus d’informations sur les chaînes de connexion, consultez : [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
     
  
6.  Cliquez sur **Informations d’identification** dans le volet gauche, puis sur **Utiliser l’authentification Windows (sécurité intégrée)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] La source de données **AdventureWorks2014** est ajoutée au volet **Données du rapport** .  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## <a name="next-task"></a>Tâche suivante  
Vous avez défini avec succès une connexion à l’exemple de base de données [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] . Vous allez ensuite créer un rapport. Voir [Leçon 3 : Définition d’un dataset destiné à un rapport de table &#40;Reporting Services&#41;](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
[Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  


