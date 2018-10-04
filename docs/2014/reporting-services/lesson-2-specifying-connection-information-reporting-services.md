---
title: 'Leçon 2 : Spécification des informations de connexion (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 75022350450358c22c53851939faa2ae7b10c8e0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200039"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Leçon 2 : Spécification des informations de connexion (Reporting Services)
  Après avoir ajouté un rapport au projet Didacticiel, vous devez définir une *source de données*, qui sont des informations de connexion que le rapport utilise pour accéder aux données à partir d’une base de données relationnelle, d’une base de données multidimensionnelle ou d’une autre ressource.  
  
 Dans cette leçon, vous allez utiliser l'exemple de base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] comme source de données. Ce didacticiel part du principe que cette base de données se trouve dans une instance par défaut du [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installée sur l’ordinateur local.  
  
### <a name="to-set-up-a-connection"></a>Pour configurer une connexion  
  
1.  Dans le volet **Données du rapport** , cliquez sur **Nouveau** , puis sur **Source de données**.  
  
    > [!NOTE]  
    >  Si le volet **Données du rapport** n’est pas visible, cliquez sur **Données du rapport** dans le menu **Affichage**.  
  
2.  Dans **nom**, type [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].  
  
3.  Vérifiez que l’option **Connexion incorporée** est sélectionnée.  
  
4.  Dans **Type**, sélectionnez **Microsoft SQL Server**.  
  
5.  Dans **Chaîne de connexion**, tapez ce qui suit :  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     Cette chaîne de connexion part du principe que [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], le serveur de rapports et la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sont tous installés sur l’ordinateur local et que vous êtes autorisé à ouvrir une session sur la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)].  
  
    > [!NOTE]  
    >  Si vous utilisez [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services ou une instance nommée, la chaîne de connexion doit comporter des informations sur l'instance :  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  Pour plus d’informations sur les chaînes de connexion, consultez [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) et [boîte de dialogue de propriétés de Source de données, général](data-source-properties-dialog-box-general.md).  
  
6.  Cliquez sur **Informations d’identification** dans le volet gauche, puis sur **Utiliser l’authentification Windows (sécurité intégrée)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] source de données [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] est ajouté à la **les données de rapport** volet.  
  
## <a name="next-task"></a>Tâche suivante  
 Vous avez défini avec succès une connexion à la [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] base de données exemple. Vous allez ensuite créer un rapport. Consultez [Leçon 3 : Définition d’un dataset destiné à un rapport de table &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
