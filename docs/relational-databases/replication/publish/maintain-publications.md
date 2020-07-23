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
ms.openlocfilehash: bde5ff877ff6ddbcb9e4e5b69953e20853a8d3e0
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86915375"
---
# <a name="maintain-publications"></a>Gestion des publications
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Une fois que vous avez créé une publication, il sera peut-être nécessaire d'ajouter ou de supprimer des articles, ou de modifier les propriétés de la publication ou des articles. La plupart des modifications sont autorisées après qu'une publication ait été créée, mais dans certains cas, il est nécessaire de générer un nouvel instantané pour une publication et/ou de réinitialiser les abonnements à la publication.
