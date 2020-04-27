---
title: 'Leçon 2 : Spécification des informations de connexion (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69d7ad1e3a65f49aa850e016e5e5bd609039ccf3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108518"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Leçon 2 : Spécification des informations de connexion (Reporting Services)
  Après avoir ajouté un rapport au projet Didacticiel, vous devez définir une *source de données*, qui sont des informations de connexion que le rapport utilise pour accéder aux données à partir d’une base de données relationnelle, d’une base de données multidimensionnelle ou d’une autre ressource.  
  
 Dans cette leçon, vous allez utiliser l'exemple de base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] comme source de données. Ce didacticiel part du principe que cette base de données se trouve dans une [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] instance par défaut de qui est installée sur votre ordinateur local.  
  
### <a name="to-set-up-a-connection"></a>Pour configurer une connexion  
  
1.  Dans le volet **données du rapport** , cliquez sur **nouveau** , puis sur **source de données...**.  
  
    > [!NOTE]  
    >  Si le volet **Données du rapport** n’est pas visible, cliquez sur **Données du rapport** dans le menu **Affichage**.  
  
2.  Dans **Nom**, tapez [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].  
  
3.  Vérifiez que l’option **Connexion incorporée** est sélectionnée.  
  
4.  Dans **Type**, sélectionnez **Microsoft SQL Server**.  
  
5.  Dans **Chaîne de connexion**, tapez ce qui suit :  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     Cette chaîne de connexion part du principe que [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], le serveur de rapports et la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sont tous installés sur l’ordinateur local et que vous êtes autorisé à ouvrir une session sur la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  
  
    > [!NOTE]  
    >  Si vous utilisez [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services ou une instance nommée, la chaîne de connexion doit comporter des informations sur l'instance :  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  Pour plus d’informations sur les chaînes de connexion, consultez [connexions de données, sources de données et chaînes de connexion dans Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) et [boîte de dialogue Propriétés de la source de données, général](data-source-properties-dialog-box-general.md).  
  
6.  Cliquez sur **Informations d’identification** dans le volet gauche, puis sur **Utiliser l’authentification Windows (sécurité intégrée)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]la source [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] de données est ajoutée au volet des **données de rapport** .  
  
## <a name="next-task"></a>Tâche suivante  
 Vous avez défini avec succès une connexion à l’exemple de base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] . Vous allez ensuite créer un rapport. Consultez [Leçon 3 : Définition d’un dataset destiné à un rapport de table &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
