---
description: À propos des pilotes et des sources de données
title: À propos des pilotes et des sources de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 141a8e99a219923fa8e658c2600e79cad6f4ae93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386585"
---
# <a name="about-drivers-and-data-sources"></a>À propos des pilotes et des sources de données
Les *pilotes* sont les composants qui traitent les requêtes ODBC et retournent des données à l’application. Si nécessaire, les pilotes modifient la demande d’une application dans un format compréhensible par la source de données. Vous devez utiliser le programme d’installation du pilote pour ajouter ou supprimer un pilote de votre ordinateur.  
  
 Les *sources de données* sont les bases de données ou les fichiers accessibles par un pilote et sont identifiés par un nom de source de données (DSN). Utilisez l’administrateur de la source de données ODBC pour ajouter, configurer et supprimer des sources de données de votre système. Les types de sources de données qui peuvent être utilisés sont décrits dans le tableau suivant.  
  
|Source de données|Description|  
|-----------------|-----------------|  
|Utilisateur|Les noms de sources de l’utilisateur sont locaux sur un ordinateur et ne peuvent être utilisés que par l’utilisateur actuel. Ils sont inscrits dans la sous-arborescence du Registre HKEY_CURRENT_USER.|  
|Système|Les noms DSN système sont locaux à un ordinateur et non dédiés à un utilisateur. Le système ou un utilisateur disposant de privilèges peut utiliser une source de données configurée avec un nom de source de données système. Les sources de noms système sont enregistrées dans la sous-arborescence du Registre HKEY_LOCAL_MACHINE.|  
|Fichier|Les sources de données de fichier sont des sources basées sur des fichiers qui peuvent être partagées entre tous les utilisateurs qui ont les mêmes pilotes installés et, par conséquent, ont accès à la base de données. Ces sources de données n’ont pas besoin d’être dédiées à un utilisateur ni à un ordinateur local. Les noms de sources de données de fichier ne sont pas identifiés par des entrées de Registre dédiées ; au lieu de cela, ils sont identifiés par un nom de fichier avec une extension. DSN.|  
  
 Les sources de données utilisateur et système sont collectivement appelées sources de données d' *ordinateur* , car elles sont locales sur un ordinateur.  
  
 Chacune de ces sources de données a un onglet dans la boîte de dialogue **administrateur de sources de données ODBC** . Pour plus d’informations sur les sources de données disponibles, consultez [Sources de données](../../odbc/reference/data-sources.md).
