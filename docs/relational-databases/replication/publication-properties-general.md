---
title: "Propriétés de la publication, Général | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.general.f1
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bb22c4211fcf7d5e07f2105f221495cbadd8d9c6
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="publication-properties-general"></a>Propriétés de la publication, Général
  La page **Général** de la boîte de dialogue **Propriétés de la publication** contient des informations générales sur la publication, notamment le nom, la description et la stratégie d'expiration d'abonnement.  
  
## <a name="options"></a>Options  
 **Nom**  
 Nom de la publication (en lecture seule).  
  
 **Base de données**  
 Nom de la base de données de publication (en lecture seule).  
  
 **Description**  
 Description de la publication.  
  
 **Type**  
 Type de la publication (en lecture seule).  
  
 **Expiration de l'abonnement**  
 Sélectionnez l'une des options d'expiration d'abonnement : **Les abonnements n'expirent jamais** ou **Les abonnements expirent**avec une période explicite (**Intervalle**).  
  
 Pour les publications d'instantané et transactionnelles, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'accepter la valeur par défaut **Les abonnements n'expirent jamais**.  
  
 Pour la réplication de fusion, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'accepter la valeur par défaut **Les abonnements expirent** et de définir une valeur aussi basse que possible pour l' **intervalle**. Lorsque la période d'expiration d'abonnement augmente, le volume des métadonnées stockées augmente également, ce qui peut affecter les performances. Déterminez la nécessité de déconnecter les abonnés ou simplement de ne pas les synchroniser pendant une longue période par rapport aux problèmes de performance associés au stockage et au traitement d'un gros volume de métadonnées.  
  
 Pour plus d’informations, consultez [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Niveau de compatibilité**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only; merge publications only. Sélectionnez la version minimale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessaire aux abonnés qui se synchronisent avec cette publication. Il existe des règles permettant de déterminer le niveau de compatibilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
