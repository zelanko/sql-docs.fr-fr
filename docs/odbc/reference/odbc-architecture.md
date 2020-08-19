---
description: Architecture d’ODBC
title: Architecture ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3afeb698d7eff9d09161a091e3de0194fea93ec2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429001"
---
# <a name="odbc-architecture"></a>Architecture d’ODBC
L’architecture ODBC comporte quatre composants :  
  
-   **Application** Effectue le traitement et appelle les fonctions ODBC pour envoyer des instructions SQL et récupérer les résultats.  
  
-   **Gestionnaire de pilotes** Charge et décharge les pilotes pour le compte d’une application. Traite les appels de fonction ODBC ou les transmet à un pilote.  
  
-   **Pilote** Traite les appels de fonction ODBC, soumet les demandes SQL à une source de données spécifique et retourne les résultats à l’application. Si nécessaire, le pilote modifie la demande d’une application afin que la demande soit conforme à la syntaxe prise en charge par le SGBD associé.  
  
-   **Source de données** Comprend les données auxquelles l’utilisateur souhaite accéder, ainsi que le système d’exploitation, le SGBD et la plateforme réseau associés (le cas échéant) utilisés pour accéder au SGBD.  
  
 Notez les points suivants sur l’architecture ODBC. Tout d’abord, plusieurs pilotes et sources de données peuvent exister, ce qui permet à l’application d’accéder simultanément aux données à partir de plusieurs sources de données. Deuxièmement, l’API ODBC est utilisée à deux emplacements : entre l’application et le gestionnaire de pilotes, et entre le gestionnaire de pilotes et chaque pilote. L’interface entre le gestionnaire de pilotes et les pilotes est parfois appelée « *interface du fournisseur de services »,* ou *SPI*. Pour ODBC, l’interface de programmation d’applications (API) et l’interface de fournisseur de services (SPI) sont les mêmes ; autrement dit, le gestionnaire de pilotes et chaque pilote ont la même interface pour les mêmes fonctions.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Applications](../../odbc/reference/applications.md)  
  
-   [Le gestionnaire de pilotes](../../odbc/reference/the-driver-manager.md)  
  
-   [Pilotes](../../odbc/reference/drivers.md)  
  
-   [Data Sources](../../odbc/reference/data-sources.md) (Sources de données)
