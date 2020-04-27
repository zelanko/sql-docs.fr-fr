---
title: Mise à jour des rapports à l’aide de classes générées à partir du schéma RDL (didacticiel SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 313a5268b754089d4ca8964328d53cb23ec6edd1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62746113"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a>Mise à jour des rapports à l'aide des classes générées à partir du schéma RDL (didacticiel SSRS)
  Ce didacticiel explique comment utiliser l’outil XML Schema Definition (XSD. exe) pour générer des classes qui vous permettent de sérialiser et de désérialiser des fichiers de définition de rapport (. rdl et. rdlc [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> ) avec la classe.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Au cours de l'étude de ce didacticiel, vous allez effectuer les opérations suivantes :  
  
-   Créez une application à l' [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aide du modèle de projet d’application console.  
  
-   Générez des classes à partir du schéma Report Definition Language (RDL) à l’aide de l’outil **xsd** .  
  
-   Se connecter à un serveur de rapports et extraire une définition de rapport.  
  
-   Écrire le code de mise à jour du fichier de définition du rapport.  
  
-   Réenregistrer la définition mise à jour du rapport sur le serveur de rapports.  
  
-   Exécutez l'application de schéma RDL (VB/C#).  
  
> [!NOTE]  
>  Les exemples de code fournis dans ce didacticiel risquent d'échouer pour les rapports ne comportant aucune description. L'échec s'explique par l'absence de la propriété de description pour les rapports pour lesquels aucune description n'est spécifiée.  
  
## <a name="requirements"></a>Conditions requises  
 Pour exécuter ce didacticiel, vous devez disposer des éléments suivants :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
-   Autorisations suffisantes pour accéder au service Web Report Server et y publier des rapports sur l'ordinateur sur lequel se trouve le serveur de rapports.  
  
-   Exemple de base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] installé sur une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Un rapport installé sur le serveur de rapports. Ce didacticiel utilise l'exemple de rapport intitulé Company Sales 2012. Pour plus d’informations sur les exemples de rapports, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
> [!NOTE]  
>  Les exemples ne sont pas installés automatiquement, mais peuvent l'être à tout moment. Pour plus d’informations sur les exemples, consultez [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).  
  
 **Durée estimée pour effectuer ce didacticiel :** 30 minutes  
  
## <a name="tasks"></a>Tâches  
 [Leçon 1 : Créer le projet Visual Studio du schéma RDL](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [Leçon 2 : Générer des classes à partir du schéma RDL à l’aide de l’outil xsd](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [Leçon 3 : Charger une définition de rapport à partir du serveur de rapports](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [Leçon 4 : Mettre à jour la définition du rapport par programmation](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [Leçon 5 : Publier la définition du rapport sur le serveur de rapports](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [Leçon 6 : exécuter l’application de schéma RDL &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [RDL (Report Definition Language) &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
