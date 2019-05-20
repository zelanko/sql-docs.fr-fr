---
title: rsModelGenerationError - Erreur Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 870f1fbc49e99e2cd43c6adb857137776c275550
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65574089"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a>rsModelGenerationError - Erreur Reporting Services
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|rsRenderingError|  
|Source de l'événement|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Composant|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Texte du message|Une erreur s'est produite lors de la génération du modèle. (rsModelGenerationError) (ReportingServicesLibrary) %1|  
  
## <a name="explanation"></a>Explication  
 Le modèle de rapport n'a pas pu être généré. Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 SP1 et les versions antérieures, cette erreur s'affiche, en règle générale, si l'objet System.Data.DataSet ne peut pas gérer une table ou une relation au sein du schéma de la base de données, par exemple lorsque deux clés étrangères sont définies sur la même colonne d'une table.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour déterminer précisément la raison pour laquelle vous avez reçu ce message, consultez les fichiers journaux du serveur de rapports qui se trouvent dans le dossier \Microsoft SQL Server\\<Instance SQL Server\>\Reporting Services\LogFiles.  
  
## <a name="internal-only"></a>Interne uniquement  
  
