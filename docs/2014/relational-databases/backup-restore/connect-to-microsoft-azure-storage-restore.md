---
title: Se connecter à Windows Azure Storage (restauration) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
caps.latest.revision: 5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 63f7f0e06a94d9d6a05995e9c19f24f0b8d46047
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172900"
---
# <a name="connect-to-windows-azure-storage-restore"></a>Se connecter au Stockage Microsoft Azure (Restauration)
  La boîte de dialogue vous permet de spécifier les informations de connexion au compte de stockage Windows Azure pour récupérer les fichiers qui y sont stockés. Après avoir spécifié les informations requises, cliquez sur **Connexion** pour établir la connexion au stockage Windows Azure.  
  
## <a name="windows-azure-storage-account"></a>Compte de stockage Windows Azure  
 **Compte de stockage**  
 Sélectionnez, entrez ou collez le nom du compte de stockage Windows Azure que vous souhaitez utiliser. La liste déroulante répertorie les comptes utilisés précédemment.  
  
 **Clé de compte**  
 Spécifiez la clé d'accès du compte de stockage Windows Azure.  
  
 Case à cocher**Utiliser des points de terminaisons sécurisés (HTTPS)**   
 Sélectionnez cette option pour établir une connexion sécurisée au stockage Windows Azure (recommandé).  
  
 Case à cocher**Enregistrer la clé de compte**   
 Cochez cette case si vous souhaitez que SQL Server se souvienne de la clé d'accès de ce compte de stockage.  
  
### <a name="sql-credential"></a>Informations d'identification SQL  
 **Sélectionner des informations d'identification existantes**  
 Sélectionnez des informations d'identification SQL existantes correspondant au compte de stockage et à la clé d'accès.  
  
 **Créer de nouvelles informations d'identification**  
 Sélectionnez cette option pour créer de nouvelles informations d'identification en utilisant les informations du compte de stockage et de la clé d'accès. Spécifiez le nom des nouvelles informations d'identification dans le champ **Nom d'identification** .  
  
  
