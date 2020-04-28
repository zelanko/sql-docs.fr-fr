---
title: Créer des informations d’identification - Authentification Azure Storage
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6de7b5c8f9cdc7162eb9c6a8ddd214d0486255c6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "70175957"
---
# <a name="create-credential---authenticate-to-azure-storage"></a>Créer des informations d’identification - Authentification Azure Storage
  Utilisez la boîte de dialogue **Sauvegarde sur un périphérique URL - Créer des informations d’identification** pour créer des informations d’identification SQL.  
  
 Lorsque vous utilisez cette boîte de dialogue pour créer des informations d’identification, vous devez ajouter un certificat de gestion Azure au magasin de certificats local, ou un profil de publication téléchargé sur votre ordinateur, pour valider l’abonnement et les informations d’identification du compte de stockage.  
  
 **Informations d'identification SQL**  
 Spécifiez le nom des informations d'identification SQL que vous souhaitez créer.  
  
## <a name="azure-credentials"></a>Informations d’identification Azure  
 **Certificat de gestion**  
 Utilisez cette option pour spécifier un certificat dans le magasin de certificats local qui correspond au certificat de gestion Azure. Pour plus d’informations sur le certificat de gestion Azure, consultez [Créer et télécharger un certificat de gestion pour Azure](https://go.microsoft.com/fwlink/?LinkId=320781).  
  
 **Abonnement**  
 Sélectionnez, entrez ou collez votre ID d’abonnement Azure qui correspond au certificat de gestion dans le magasin de certificats local.  
  
 **Profil de publication**  
 Utilisez cette option si vous avez un profil de publication téléchargé sur votre ordinateur. Si vous utilisez cette option, l'ID d'abonnement et le certificat sont remplis automatiquement.  
  
> [!CAUTION]  
>  SQL Server prend actuellement en charge la version 2.0 du profil de publication. Pour télécharger la version prise en charge du profil de publication, consultez [Télécharger le profil de publication 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
  
## <a name="storage-account"></a>Compte de stockage  
 Sélectionnez le compte de stockage que vous souhaitez utiliser pour stocker les fichiers de sauvegarde.  
  
  
