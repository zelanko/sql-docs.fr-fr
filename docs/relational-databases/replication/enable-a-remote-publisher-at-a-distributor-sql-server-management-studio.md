---
title: Activer un serveur de publication distant sur le serveur de distribution (SSMS)
description: Découvrez comment activer un serveur de publication distant sur le serveur de distribution dans SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- remote Distributors [SQL Server replication]
- Publishers [SQL Server replication]
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 3633ff588a8d7252b78f5a2510eaad96f7c1eb64
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460252"
---
# <a name="enable-a-remote-publisher-at-a-distributor-sql-server-management-studio"></a>activer un serveur de publication distant sur un serveur de distribution (SQL Server Management Studio)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Activer un serveur de publication afin d'utiliser un serveur de distribution distant sur la page **Serveurs de publication** . Cette page est disponible dans l’Assistant Configuration de la distribution et la boîte de dialogue **Propriétés du serveur de distribution - \<Distributor>** . Pour plus d’informations sur l’utilisation de l’Assistant et l’accès à la boîte de dialogue, consultez [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md) et [Afficher et modifier les propriétés du serveur de distribution et du serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-enable-a-publisher-in-the-configure-distribution-wizard"></a>Pour activer un serveur de publication dans l'Assistant Configuration de distribution  
  
1.  Sur la page **Serveurs de publication** de l'Assistant Configuration de publication, cliquez sur **Ajouter**.  
  
2.  Cliquez sur **Ajouter un serveur de publication SQL Server**. Pour plus d'informations sur l'activation d'un serveur de publication Oracle pour utiliser un serveur de distribution, consultez [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  Dans la boîte de dialogue **Se connecter au serveur** , indiquez les informations de connexion du serveur de publication qui utilisera le serveur de distribution distant, plus cliquez sur **Se connecter**.  
  
4.  Sur la page **Mot de passe du serveur de distribution** , dans les zones de texte **Mot de passe** et **Confirmer le mot de passe** , spécifiez un mot de passe fort pour le compte **distributor_admin** que la réplication utilise pour se connecter du serveur de publication sur le serveur de distribution afin d'effectuer des tâches administratives.  
  
5.  Pour afficher et modifier les paramètres d’un serveur de publication, cliquez sur le bouton des propriétés ( **...** ).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

### <a name="to-enable-a-publisher-in-the-distributor-properties-dialog-box"></a>Pour activer un serveur de publication dans la boîte de dialogue Propriétés du serveur de distribution  
  
1.  Dans la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution - \<Distributor>** , cliquez sur **Ajouter**.  
  
2.  Cliquez sur **Ajouter un serveur de publication SQL Server**. Pour plus d'informations sur l'activation d'un serveur de publication Oracle pour utiliser un serveur de distribution, consultez [Create a Publication from an Oracle Database](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  Dans la boîte de dialogue **Se connecter au serveur** , indiquez les informations de connexion du serveur de publication qui utilisera le serveur de distribution distant, plus cliquez sur **Se connecter**.  
  
4.  Sur la page **Serveurs de publication** , dans les zones de texte **Mot de passe** et **Confirmer le mot de passe** , spécifiez un mot de passe fort pour le compte **distributor_admin** que la réplication utilise pour se connecter du serveur de publication sur le serveur de distribution afin d'effectuer des tâches administratives.  
  
5.  Pour afficher et modifier les paramètres d’un serveur de publication, cliquez sur le bouton des propriétés ( **...** ).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Sécuriser le serveur de distribution](../../relational-databases/replication/security/secure-the-distributor.md)  
  
  
