---
title: Créer un projet SMO Visual c# dans Visual Studio .NET | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2bc775f7f857bffb5a7840d99de00fc546e71d03
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717987"
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Comment créer un projet SMO Visual C# dans Visual Studio .NET
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Cette section décrit comment élaborer une application de console SMO simple.  
  
 Cet exemple importe des espaces de noms, qui permettent au programme de référencer des types SMO. L’importation de la **Agent** espace de noms est facultative. Utilisez-le lorsque vous écrivez un programme qui utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Le **commune** espace de noms est requis pour établir une connexion sécurisée à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le **SqlClient** espace de noms est utilisé pour traiter les erreurs d’exception SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Création d'un projet SMO Visual C# dans Visual Studio.NET  
  
1. Démarrez Visual Studio
  
2. Sur le **fichier** menu, cliquez sur **New** , puis **projet**.  La boîte de dialogue **Nouveau projet** s'affiche.   
  
3. Dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **installé** volet, accédez à **modèles**\\**Visual C#**\\**Windows** Sélectionnez **Application Console**.  
  
4. (Facultatif) Dans le **nom** texte, tapez le nom de la nouvelle application.  

5. Cliquez sur **OK** pour charger le modèle d’application de console.  

6. Suivez les instructions de [l’installation de SMO](installing-smo.md) pour installer le package pour votre projet à référencer.
  
7. Dans le menu **Affichage** , cliquez sur **Code**.
    
8. Dans le code, avant l’instruction d’espace de noms, tapez la commande suivante **à l’aide de** instructions pour qualifier les types dans l’espace de noms SMO :
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO comporte différents espaces de noms sous Microsoft.SqlServer.Management.Smo, par exemple Microsoft.SqlServer.Management.Smo.Agent. Ajoutez ces espaces de noms lorsqu'ils sont requis.  
  
16. Vous pouvez à présent ajouter votre code SMO.  
  
  
