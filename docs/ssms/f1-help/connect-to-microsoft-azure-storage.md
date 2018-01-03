---
title: Se connecter au service Stockage Microsoft Azure | Microsoft Docs
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-f1
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: 
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 21933a1a1cad8a6681bf2324cd510290031fa5d2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="connect-to-microsoft-azure-storage"></a>Se connecter au service Stockage Microsoft Azure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Utilisez la boîte de dialogue **Connexion de stockage Windows Azure** pour spécifier un compte de stockage et valider votre connexion à Windows Azure.  
  
## <a name="options"></a>Options  
Spécifiez les informations suivantes sur votre compte Windows Azure, puis cliquez sur **Suivant** pour continuer.  
  
1.  **Compte de stockage** - Spécifiez le nom du compte de stockage.

   >[!NOTE]
   > Vous pouvez uniquement vous connecter à des [comptes de stockage à usage général](https://docs.microsoft.com/en-us/azure/storage/storage-introduction#introducing-the-azure-storage-services). La connexion à d’autres types de comptes de stockage peut entraîner une erreur similaire à celle qui suit :
   >
   >  Le format de la valeur d’un des en-têtes HTTP n’est pas correct. (Microsoft.SqlServer.StorageClient).
   >
   >  Le serveur distant a retourné une erreur : (400) Requête incorrecte. (Système)

2.  **Clé de compte** - Indiquez la clé de compte pour le compte de stockage spécifié.  
  
3.  **Utiliser des points de terminaison sécurisés (HTTPS)** – Cette option utilise la communication chiffrée et l’identification sécurisée d’un serveur web du réseau.  
  
4.  **Enregistrer la clé de compte** - Cette option enregistre votre mot de passe dans un fichier chiffré.  
  
