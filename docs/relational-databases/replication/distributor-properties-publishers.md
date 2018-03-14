---
title: "Propriétés du serveur de distribution, Serveurs de publication | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.distproperties.publishers.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 74c5349f17f7802c55ccf1c21061f966896244d8
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="distributor-properties-publishers"></a>Propriétés du serveur de distribution, Serveurs de publication
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution** vous permet de faire en sorte que les serveurs de publication utilisent ce serveur de distribution. Vous pouvez également définir les propriétés associées à ces serveurs de publication. Notez que l'activation d'un serveur de publication pour utiliser ce serveur en tant que serveur de distribution distant ne fait pas de ce serveur un serveur de publication. Vous devez vous connecter au serveur de publication, le configurer pour la publication, et choisir ce serveur comme distributeur. Vous pouvez configurer le serveur de publication et choisir un serveur de distribution à l'aide de l'Assistant Nouvelle publication.  
  
## <a name="options"></a>Options  
 **Serveurs de publication**  
 Sélectionnez les serveurs autorisés à utiliser ce serveur de distribution. Cliquez sur le bouton Propriétés **(...)** situé en regard d'un serveur de publication pour voir et définir d'autres propriétés.  
  
 **Ajouter**  
 Si le serveur souhaité ne figure pas dans la liste, cliquez sur **Ajouter** afin d'ajouter un serveur de publication [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Oracle Publisher à la liste des serveurs de publication disponibles. Si le serveur ajouté est le premier à utiliser ce serveur de distribution en tant que serveur de distribution distant, vous serez invité à fournir un mot de passe de lien d'administration.  
  
 **Mot de passe du lien d'administration**  
 Permet de spécifier ou de mettre à jour le mot de passe utilisé pour assurer la réplication de connexion entre le serveur de publication et le serveur de distribution distant à l'aide de la connexion **distributor_admin** :  
  
-   Si le serveur de distribution sert uniquement au niveau local, ce mot de passe est généré de manière aléatoire et configuré automatiquement.  
  
-   Si le serveur de distribution possède déjà un serveur de publication distant, un mot de passe a déjà été fourni sur cette page ou la page **Mot de passe du serveur de distribution** de l'Assistant Configuration de la distribution.  
  
-   Si vous activez le premier serveur de publication distant pour ce serveur de distribution, vous serez invité à entrer un mot de passe.  
  
 Pour plus d’informations sur la sécurité des serveurs de distribution, consultez [Sécuriser le serveur de distribution](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
