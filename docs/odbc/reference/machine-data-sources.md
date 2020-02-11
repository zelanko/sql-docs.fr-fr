---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fe58e6e560ce4a538290b9f87e99bb4f22e12aab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68062645"
---
# <a name="machine-data-sources"></a>Sources de données de machine
Les *sources de données* de l’ordinateur sont stockées sur le système avec un nom défini par l’utilisateur. Les informations associées au nom de la source de données sont toutes les informations dont le gestionnaire de pilotes et le pilote ont besoin pour se connecter à la source de données. Pour une source de données xBase, il peut s’agir du nom du pilote xbase, du chemin d’accès complet du répertoire contenant les fichiers xbase et de certaines options qui indiquent au pilote comment utiliser ces fichiers, tels que le mode mono-utilisateur ou en lecture seule. Pour une source de données Oracle, il peut s’agir du nom du pilote Oracle, du serveur où se trouve le SGBD Oracle, de la chaîne de connexion SQL * NET qui identifie\*le pilote réseau SQL à utiliser et de l’ID système de la base de données sur le serveur.
