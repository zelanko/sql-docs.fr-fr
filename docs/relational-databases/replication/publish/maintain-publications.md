---
title: Gestion des publications | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- maintaining publications [SQL Server replication]
- publications [SQL Server replication], maintaining
- administering replication, publications
ms.assetid: d5bf7340-2b0b-4593-965c-de04ae628344
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 92e24c3ac193c3229cd61b098ff7c3287c7de998
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159897"
---
# <a name="maintain-publications"></a>Gestion des publications
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  Une fois que vous avez créé une publication, il sera peut-être nécessaire d'ajouter ou de supprimer des articles, ou de modifier les propriétés de la publication ou des articles. La plupart des modifications sont autorisées après qu'une publication ait été créée, mais dans certains cas, il est nécessaire de générer un nouvel instantané pour une publication et/ou de réinitialiser les abonnements à la publication.
