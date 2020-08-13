---
title: Se connecter au service Stockage Microsoft Azure
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 07/12/2017
ms.openlocfilehash: f88bafe27da30ceec6154bf64cd9ced0046f7e87
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87123080"
---
# <a name="connect-to-microsoft-azure-storage"></a>Se connecter au service Stockage Microsoft Azure

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Utilisez la boîte de dialogue **Connexion de stockage Azure** pour spécifier un compte de stockage et valider votre connexion à Azure.  
  
## <a name="options"></a>Options  
Spécifiez les informations suivantes sur votre compte Azure, puis cliquez sur **Suivant** pour continuer.  
  
1.  **Compte de stockage** - Spécifiez le nom du compte de stockage.

   >[!NOTE]
   > Vous pouvez uniquement vous connecter à des [comptes de stockage à usage général](https://docs.microsoft.com/azure/storage/common/storage-introduction#azure-storage-services). La connexion à d’autres types de comptes de stockage peut entraîner une erreur similaire à celle qui suit :
   >
   >  The value for one of the HTTP headers is not in the correct format. (Le format de la valeur d’un des en-têtes HTTP est incorrect.) (Microsoft.SqlServer.StorageClient).
   >
   >  Le serveur distant a retourné une erreur : (400) Requête incorrecte. (Système)

2.  **Clé de compte** - Indiquez la clé de compte pour le compte de stockage spécifié.  
  
3.  **Utiliser des points de terminaison sécurisés (HTTPS)** - Cette option utilise la communication chiffrée et l’identification sécurisée d’un serveur web du réseau.  
  
4.  **Enregistrer la clé de compte** - Cette option enregistre votre mot de passe dans un fichier chiffré.  
  
