---
title: Créer un projet Visual Basic SMO dans Visual Studio .NET | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic [SMO]
ms.assetid: d7a3892c-0f1c-4c4d-8480-b58dce3720bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 49eb94833d10b2e901c008092aea29eab8e4ad48
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933680"
---
# <a name="create-a-visual-basic-smo-project-in-visual-studio-net"></a>Créer un projet SMO Visual Basic dans Visual Studio .NET
  Cette section décrit comment élaborer une application de console SMO simple.  
  
 Cet exemple importe des espaces de noms, qui permettent au programme de référencer des types SMO. L'importation de l'espace de noms `Agent` est facultative. Utilisez-le quand vous écrivez un programme qui utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’agent. L'espace de noms `Common` est requis pour établir une connexion sécurisée avec l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'espace de noms `SqlClient` est utilisé pour traiter les erreurs d'exception SQL.  
  
### <a name="creating-a-visual-basic-smo-project-in-visual-studionet"></a>Création d'un projet SMO Visual Basic dans Visual Studio.NET  
  
1.  Démarrez [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (ou [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).  
  
2.  Dans le menu **Fichier**, cliquez sur **Nouveau projet**. La boîte de dialogue **Nouveau projet** apparaît.  
  
3.  Dans la boîte de dialogue **types de projets** , sélectionnez **Visual Basic**, puis sélectionnez **Windows**. Dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] volet Modèles installés, sélectionnez **application console.**  
  
4.  Facultatif Dans le champ **nom** , tapez le nom de la nouvelle application.  
  
5.  Cliquez sur **OK** pour charger le [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] modèle application console.  
  
6.  Dans le menu **Projet**, sélectionnez **Ajouter une référence**. La boîte de dialogue **Ajouter une référence** s’affiche.  
  
7.  Cliquez sur **Parcourir**, recherchez les assemblys Smo dans le dossier C:\Program Files\Microsoft SQL Server\120\SDK\Assemblies, puis sélectionnez les fichiers suivants. Il s'agit des fichiers minimum requis pour générer une application SMO :  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc  
  
    > [!NOTE]  
    >  Utilisez la touche `Ctrl` pour sélectionner plusieurs fichiers.  
  
8.  Ajoutez les autres assemblys SMO qui sont nécessaires. Par exemple, si vous programmez spécifiquement [!INCLUDE[ssSB](../../includes/sssb-md.md)], ajoutez les assemblys suivants :  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. Cliquez sur **Ouvrir**.  
  
10. Dans le menu **affichage** , cliquez sur **code**.-ou-sélectionnez la fenêtre Module1. vb pour afficher la fenêtre de code.  
  
11. Dans le code, avant les déclarations, tapez les instructions **Imports** suivantes pour qualifier les types dans l’espace de noms Smo.  
  
    ```  
    Imports Microsoft.SqlServer.Management.Smo  
    Imports Microsoft.SqlServer.Management.Common  
    ```  
  
12. SMO comporte différents espaces de noms sous Microsoft.SqlServer.Management.Smo, par exemple Microsoft.SqlServer.Management.Smo.Agent. Ajoutez ces espaces de noms lorsqu'ils sont requis.  
  
13. Vous pouvez à présent ajouter votre code SMO.  
  
  
