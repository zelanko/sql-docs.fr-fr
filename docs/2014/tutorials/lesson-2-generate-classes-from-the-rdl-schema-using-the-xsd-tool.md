---
title: 'Leçon 2 : générer des classes à partir du schéma RDL à l’aide de l’outil XSD | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f5f74c6621d329885e9149fce9a37c7418d9c37b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62653753"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a>Leçon 2 : Générer des classes à partir du schéma RDL à l’aide de l’outil xsd
  Une fois que vous avez créé votre projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], l'étape suivante consiste à extraire une copie locale du schéma de la définition du rapport et à exécuter l'outil de définition du schéma XML (Xsd.exe).  
  
### <a name="to-generate-the-rdl-classes"></a>Pour générer les classes RDL  
  
1.  Ouvrez une instance d' [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (ou un navigateur Web équivalent) et accédez à l’URL suivante :  
  
    ```  
    https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  Une fois le schéma RDL ouvert dans le navigateur, accédez au menu **fichier** , puis sélectionnez **Enregistrer sous**.  
  
3.  Accédez à l'emplacement où vous avez créé votre projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et enregistrez le schéma avec le nom de fichier ReportDefinition.xsd.  
  
4.  Une fois le fichier enregistré, ouvrez une instance de l' [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] invite de commandes. Pour ouvrir une instance de l’invite de commandes, cliquez sur le menu Démarrer, pointez sur **tous les programmes**, pointez sur **Microsoft Visual Studio 2010**, sur **Visual Studio Tools** , puis cliquez sur **invite de commandes de Visual Studio (2010)**.  
  
5.  Remplacez le chemin d'accès en cours par l'emplacement où vous avez enregistré le fichier ReportDefinition.xsd :  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  Générez le fichier ReportDefinition.cs qui contient les classes du schéma RDL à l'aide de la commande suivante :  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     Pour générer un fichier ReportDefinition.vb, utilisez la commande ci-après :  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  Ajoutez ReportDefinition.xsd à votre projet. Dans le menu **projet** , cliquez sur **Ajouter un élément existant**. Accédez à l’emplacement du fichier fichier ReportDefinition. xsd, sélectionnez fichier ReportDefinition. xsd, puis cliquez sur **Ajouter**.  
  
    > [!NOTE]  
    >  Une fois que vous avez ajouté le fichier fichier ReportDefinition. xsd au projet, vous remarquerez dans **Explorateur de solutions** que le fichier ReportDefinition.cs (. vb) n’y figure pas. Pour afficher le fichier, cliquez sur le bouton Développer/Réduire en regard du fichier ReportDefinition.xsd.  
  
## <a name="next-lesson"></a>Leçon suivante  
 Dans la prochaine leçon, vous allez écrire du code pour charger une définition de rapport à partir d'un serveur de rapports à l'aide des classes que vous avez générées depuis le schéma RDL. Consultez [la leçon 3 : charger une définition de rapport à partir du serveur de rapports](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des rapports à l’aide de classes générées à partir du schéma RDL &#40;didacticiel SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [RDL (Report Definition Language) &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
