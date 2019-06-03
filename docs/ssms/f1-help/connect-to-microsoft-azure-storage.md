---
title: Se connecter au service Stockage Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2c4381ddbbe0a218b6fc53d8e054017b66068b59
ms.sourcegitcommit: 944af0f6b31bf07c861ddd4d7960eb7f018be06e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454553"
---
# <a name="connect-to-microsoft-azure-storage"></a>Se connecter au service Stockage Microsoft Azure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Utilisez la boîte de dialogue **Connexion de stockage Windows Azure** pour spécifier un compte de stockage et valider votre connexion à Windows Azure.  
  
## <a name="options"></a>Options  
Spécifiez les informations suivantes sur votre compte Windows Azure, puis cliquez sur **Suivant** pour continuer.  
  
1.  **Compte de stockage** - Spécifiez le nom du compte de stockage.

   >[!NOTE]
   > Vous pouvez uniquement vous connecter à des [comptes de stockage à usage général](https://docs.microsoft.com/azure/storage/storage-introduction#azure-storage-services). La connexion à d’autres types de comptes de stockage peut entraîner une erreur similaire à celle qui suit :
   >
   >  Le format de la valeur d’un des en-têtes HTTP n’est pas correct. (Microsoft.SqlServer.StorageClient).
   >
   >  Le serveur distant a retourné une erreur : (400) Requête incorrecte. (Système)

2.  **Clé de compte** - Indiquez la clé de compte pour le compte de stockage spécifié.  
  
3.  **Utiliser des points de terminaison sécurisés (HTTPS)** - Cette option utilise la communication chiffrée et l’identification sécurisée d’un serveur web du réseau.  
  
4.  **Enregistrer la clé de compte** - Cette option enregistre votre mot de passe dans un fichier chiffré.  
  
