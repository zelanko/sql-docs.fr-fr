---
description: Sources de données de machine
title: Sources de données de l’ordinateur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- machine data sources [ODBC]
- data sources [ODBC], machine
ms.assetid: 371bb5b5-1258-4657-acb5-d2b688b2ab4c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f77a9a47dc6d5b0ffd29021b756f9b0538bfdea3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499672"
---
# <a name="machine-data-sources"></a>Sources de données de machine
Les *sources de données* de l’ordinateur sont stockées sur le système avec un nom défini par l’utilisateur. Les informations associées au nom de la source de données sont toutes les informations dont le gestionnaire de pilotes et le pilote ont besoin pour se connecter à la source de données. Pour une source de données xBase, il peut s’agir du nom du pilote xbase, du chemin d’accès complet du répertoire contenant les fichiers xbase et de certaines options qui indiquent au pilote comment utiliser ces fichiers, tels que le mode mono-utilisateur ou en lecture seule. Pour une source de données Oracle, il peut s’agir du nom du pilote Oracle, du serveur où se trouve le SGBD Oracle, de la chaîne de connexion SQL * NET qui identifie le \* pilote réseau SQL à utiliser et de l’ID système de la base de données sur le serveur.
