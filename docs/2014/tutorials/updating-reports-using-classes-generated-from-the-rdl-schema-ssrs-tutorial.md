---
title: La mise à jour des rapports à l’aide des Classes générées à partir du schéma RDL (didacticiel SSRS) | Microsoft Docs
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
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014040"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a>Mise à jour des rapports à l'aide des classes générées à partir du schéma RDL (didacticiel SSRS)
  Ce didacticiel illustre comment utiliser le XML Schema Definition Tool (Xsd.exe) pour générer des classes qui vous permettent de sérialiser et désérialiser les fichiers de définition de rapport (.rdl et .rdlc) avec le [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> classe.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Au cours de l'étude de ce didacticiel, vous allez effectuer les opérations suivantes :  
  
-   Créer une application qui utilise le [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modèle de projet Application Console.  
  
-   Générer des classes du schéma de langage RDL (Report Definition) à l’aide de la **xsd** outil.  
  
-   Se connecter à un serveur de rapports et extraire une définition de rapport.  
  
-   Écrire le code de mise à jour du fichier de définition du rapport.  
  
-   Réenregistrer la définition mise à jour du rapport sur le serveur de rapports.  
  
-   Exécutez l'application de schéma RDL (VB/C#).  
  
> [!NOTE]  
>  Les exemples de code fournis dans ce didacticiel risquent d'échouer pour les rapports ne comportant aucune description. L'échec s'explique par l'absence de la propriété de description pour les rapports pour lesquels aucune description n'est spécifiée.  
  
## <a name="requirements"></a>Configuration requise  
 Pour exécuter ce didacticiel, vous devez disposer des éléments suivants :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
-   Autorisations suffisantes pour accéder au service Web Report Server et y publier des rapports sur l'ordinateur sur lequel se trouve le serveur de rapports.  
  
-   Exemple de base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] installé sur une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Un rapport installé sur le serveur de rapports. Ce didacticiel utilise l'exemple de rapport intitulé Company Sales 2012. Pour plus d’informations sur les exemples de rapports, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
> [!NOTE]  
>  Les exemples ne sont pas installés automatiquement, mais peuvent l'être à tout moment. Pour plus d’informations sur les exemples, consultez [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).  
  
 **Durée estimée pour effectuer le tutoriel :** 30 minutes  
  
## <a name="tasks"></a>Tâches  
 [Leçon 1 : Créer le projet Visual Studio du schéma RDL](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [Leçon 2 : Générer des Classes à partir du schéma RDL à l’aide de l’outil xsd](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [Leçon 3 : Charger une définition de rapport du serveur de rapports](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [Leçon 4 : Mettre à jour la définition de rapport par programme](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [Leçon 5 : Publier la définition de rapport sur le serveur de rapports](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [Leçon 6 : Exécutez l’Application du schéma RDL &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [RDL (Report Definition Language) &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
