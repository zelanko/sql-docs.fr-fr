---
title: Créer des informations d’identification - Authentification Azure Storage
description: Dans SQL Server, utilisez la page Créer des informations d’identification de la boîte de dialogue Sauvegarder la base de données pour fournir un certificat de gestion Azure en vue de valider votre connexion.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
author: cawrites
ms.author: chadam
ms.openlocfilehash: 331d973e3290c5528ba811f7d6306f7505b55041
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "96129262"
---
# <a name="create-credential---authenticate-to-azure-storage"></a>Créer des informations d’identification - Authentification Azure Storage
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Utilisez la boîte de dialogue **Sauvegarde sur un périphérique URL - Créer des informations d’identification** pour créer des informations d’identification SQL.  
  
 Lorsque vous utilisez cette boîte de dialogue pour créer des informations d’identification, vous devez ajouter un certificat de gestion Azure au magasin de certificats local, ou un profil de publication téléchargé sur votre ordinateur, pour valider l’abonnement et les informations d’identification du compte de stockage.  
  
 **Informations d'identification SQL**  
 Spécifiez le nom des informations d'identification SQL que vous souhaitez créer.  
  
## <a name="azure-credentials"></a>Informations d’identification Azure  
 **Certificat de gestion**  
 Utilisez cette option pour spécifier un certificat dans le magasin de certificats local qui correspond au certificat de gestion Azure. Pour plus d’informations sur le certificat de gestion Azure, consultez [Créer et télécharger un certificat de gestion pour Azure](/previous-versions/azure/gg551722(v=azure.100)).  
  
 **Abonnement**  
 Sélectionnez, entrez ou collez votre ID d’abonnement Azure qui correspond au certificat de gestion dans le magasin de certificats local.  
  
 **Profil de publication**  
 Utilisez cette option si vous avez un profil de publication téléchargé sur votre ordinateur. Si vous utilisez cette option, l'ID d'abonnement et le certificat sont remplis automatiquement.  
  
> [!CAUTION]  
>  SQL Server prend actuellement en charge la version 2.0 du profil de publication. Pour télécharger la version prise en charge du profil de publication, consultez [Télécharger le profil de publication 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
  
## <a name="storage-account"></a>Compte de stockage  
 Sélectionnez le compte de stockage que vous souhaitez utiliser pour stocker les fichiers de sauvegarde.  
  
