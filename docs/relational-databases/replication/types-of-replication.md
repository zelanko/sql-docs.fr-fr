---
title: Types de réplication | Microsoft Docs
description: Découvrez les différents types de réplication que SQL Server fournit pour une utilisation dans des applications distribuées.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016
ms.openlocfilehash: a1f72eeaa2ffff2db3e536eec6f1aa317a2cb45c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97468700"
---
# <a name="types-of-replication"></a>Types de réplication
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit les types de réplication suivants à utiliser dans des applications distribuées :  

| **Type** | **Description** |
|:-------- | :-------------- |
| [Réplication transactionnelle](transactional/transactional-replication.md)| Les changements apportés au serveur de publication sont remis à l’Abonné au fur et à mesure qu’ils se produisent (en quasi temps réel). Les changements de données sont appliqués à l’Abonné dans le même ordre et selon les mêmes limites de transaction que sur le serveur de publication. | 
| [Réplication de fusion](merge/merge-replication.md) | Les données peuvent être modifiées sur le serveur de publication et sur l’Abonné, et sont suivies avec des déclencheurs. L'abonné est synchronisé avec l'éditeur lorsqu'il est connecté au réseau et il échange toutes les lignes qui ont changé entre l'éditeur et l'abonné depuis la dernière synchronisation. | 
| [Réplication d’instantané](snapshot-replication.md) | Applique un instantané du serveur de publication à l’Abonné, qui distribue les données telles qu’elles apparaissent à un moment précis, sans superviser les mises à jour des données. Lors de la synchronisation, l'intégralité de l'instantané est générée et envoyée aux abonnés.| 
| [Égal à égal](transactional/peer-to-peer-transactional-replication.md) | Conçue sur la base de la réplication transactionnelle, la réplication d’égal à égal propage les modifications en quasi temps réel de manière transactionnelle entre plusieurs instances de serveur. | 
| [Bidirectionnelle](transactional/bidirectional-transactional-replication.md)| Une réplication transactionnelle bidirectionnelle est une topologie de réplication transactionnelle spécifique qui permet à deux serveurs d'échanger des modifications : chaque serveur publie des données puis s'abonne à une publication contenant les mêmes données provenant de l'autre serveur. | 
| [Abonnements pouvant être mis à jour](transactional/updatable-subscriptions-for-transactional-replication.md) | Ce type repose sur la réplication transactionnelle. Quand des données sont mises à jour sur un Abonné pour un abonnement pouvant être mis à jour, elles sont d’abord propagées au serveur de publication, puis aux autres Abonnés. | 
  
 
Le type de réplication que vous choisissez pour une application dépend de nombreux facteurs, dont l'environnement physique de la réplication, le type et la quantité de données à répliquer et si les données sont ou non mises à jour sur l'Abonné. L'environnement physique comprend le nombre et l'emplacement des ordinateurs impliqués dans la réplication et le fait que ces ordinateurs sont des clients (stations de travail, ordinateurs portables ou ordinateurs de poche) ou des serveurs.  
  
Chaque type de réplication commence par une synchronisation initiale des objets publiés entre le serveur de publication et les Abonnés. Cette synchronisation peut être effectuée par réplication avec un *instantané*, qui est une copie de tous les objets et de toutes les données spécifiées par une publication. Quand l'instantané est créé, il est remis aux Abonnés. Pour certaines applications, la réplication d'instantané est tout ce qui est requis. Pour d'autres types d'applications, il est important que les modifications de données suivantes soient transmises à l'Abonné de façon incrémentielle au fil du temps. Certaines applications requièrent aussi que les modifications transitent en sens inverse, de l'Abonné vers le serveur de publication. La réplication transactionnelle et la réplication de fusion comportent des options pour ces types d'applications.  
  
 
## <a name="see-also"></a>Voir aussi  
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)
  
  
