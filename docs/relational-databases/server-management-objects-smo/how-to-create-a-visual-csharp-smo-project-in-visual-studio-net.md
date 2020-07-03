---
title: Créer un projet SMO Visual C# dans Visual Studio .NET
ms.custom: seo-dt-2019
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 60d0f5b55664312be1bdf6501cf54e78a826434b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900637"
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Comment créer un projet SMO Visual C# dans Visual Studio .NET
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

  Cette section décrit comment élaborer une application de console SMO simple.  
  
 Cet exemple importe des espaces de noms, qui permettent au programme de référencer des types SMO. L’importation de l’espace de noms de l' **agent** est facultative. Utilisez-le quand vous écrivez un programme qui utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’agent. L’espace de noms **commun** est requis pour établir une connexion sécurisée à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L’espace de noms **SqlClient** est utilisé pour traiter les erreurs d’exception SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Création d'un projet SMO Visual C# dans Visual Studio.NET  
  
1. Démarrez Visual Studio
  
2. Dans le menu **fichier** , cliquez sur **nouveau** , puis sur **projet**.  La boîte de dialogue **Nouveau projet** apparaît.   
  
3. Dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] volet **installé** , accédez à **modèles** \\ **Windows Visual C#**, \\ **Windows** puis sélectionnez **application console**.  
  
4. Facultatif Dans la zone de texte **nom** , tapez le nom de la nouvelle application.  

5. Cliquez sur **OK** pour charger le modèle application console.  

6. Suivez les instructions de la procédure d' [installation de Smo](installing-smo.md) pour installer le package à référencer dans votre projet.
  
7. Dans le menu **Affichage** , cliquez sur **Code**.
    
8. Dans le code, avant l’instruction d’espace de noms, tapez les instructions **using** suivantes pour qualifier les types dans l’espace de noms SMO :
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO comporte différents espaces de noms sous Microsoft.SqlServer.Management.Smo, par exemple Microsoft.SqlServer.Management.Smo.Agent. Ajoutez ces espaces de noms lorsqu'ils sont requis.  
  
16. Vous pouvez à présent ajouter votre code SMO.  

