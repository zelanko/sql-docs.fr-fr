---
description: Historique des pilotes pour les bases de données de poste de travail
title: Historique des pilotes de base de données de bureau | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], history
- ODBC desktop database drivers [ODBC], history
- desktop database drivers [ODBC], history
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80e8f1b52abac92ba09b97d35d45dfe0506963ec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500322"
---
# <a name="history-of-the-desktop-database-drivers"></a>Historique des pilotes pour les bases de données de poste de travail
Le tableau suivant présente l’historique des versions des pilotes de base de données de bureau.  
  
|Version|Date de sortie|Description|  
|-------------|------------------|-----------------|  
|1.0|1993 août|Utilisé le processeur de requêtes SIMBA généré par le logiciel PageAhead. SIMBA a reçu des appels ODBC et des instructions SQL, les a traités dans des appels ISAM installables Microsoft Jet, puis appelé couche de distribution ISAM Microsoft Jet pour charger et appeler le pilote ISAM installable approprié.|  
|2.0|1994 décembre|Utilisé avec ODBC 2,0, qui a considérablement étendu les fonctionnalités ODBC. La modification majeure de la version 2,0 était que le moteur de base de données Microsoft Jet remplace le processeur de requêtes SIMBA. Avec le moteur de base de données Microsoft Jet, les pilotes de base de données de bureau sont intégrés plus étroitement aux pilotes ISAM Microsoft Jet installables et à la technologie Microsoft Access. Des améliorations significatives ont été apportées :<br /><br /> -Prise en charge native des curseurs à défilement.<br />-Prise en charge native des jointures externes, des jointures pouvant être mises à jour et hétérogènes et des transactions.<br />-versions 32 bits des pilotes pour Microsoft Windows NT.|  
|3.0|1995 octobre|Prise en charge fournie pour Windows 95 et Windows NT Workstation ou NT Server 3,51. Seuls les pilotes 32 bits ont été inclus dans cette version ; les pilotes 16 bits pour Windows version 3,1 ont été supprimés.|  
|3,5|1996 octobre|Ces pilotes étaient compatibles avec le jeu de caractères codés sur deux octets (DBCS), ils étaient mieux adaptés à une utilisation avec les applications Internet que les versions précédentes et permettaient d’utiliser des noms de sources de données de fichiers (DSN). Le pilote Microsoft Access a été publié dans une version RISC pour une utilisation sur les plateformes alpha pour Windows 95/98 et Windows NT 3,51 et les systèmes d’exploitation ultérieurs.|  
|4.0|Fin 1998|Prend en charge le format Unicode du moteur Microsoft Jet, ainsi que la compatibilité pour le format ANSI des versions antérieures.|  
  
> [!NOTE]  
>  Les pilotes version 3.5 ont été conçus pour fonctionner avec ODBC2. *x*. Bien qu’elles fonctionnent également avec ODBC 3,0, elles ne prennent pas en charge toutes les fonctionnalités ODBC 3,0. Pour plus d’informations sur la façon dont ces pilotes fonctionnent avec ODBC 3,0, consultez [compatibilité descendante et conformité aux normes](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).
