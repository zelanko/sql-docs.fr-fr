---
title: Architecture du conducteur (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], architecture
ms.assetid: c5003413-0cc1-4f41-b877-a64e2f5ab118
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ffe2023f028357468700b9bd995d22129ba06817
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294219"
---
# <a name="driver-architecture"></a>Architecture des pilotes
L’architecture du conducteur se divise en deux catégories, selon les processus logiciels énoncés sqL :  
  
-   **Pilotes basés sur les fichiers** Le conducteur accède directement aux données physiques. Dans ce cas, le conducteur agit à la fois comme conducteur et source de données; c’est-à-dire qu’il traite les appels de l’ODBC et les déclarations SQL. Par exemple, les pilotes dBASE sont des pilotes basés sur des fichiers parce que dBASE ne fournit pas un moteur de base de données autonome que le conducteur peut utiliser. Il est important de noter que les développeurs de pilotes basés sur des fichiers doivent écrire leurs propres moteurs de base de données.  
  
-   **Pilotes basés sur DBMS** Le conducteur accède aux données physiques par l’intermédiaire d’un moteur de base de données distinct. Dans ce cas, le conducteur ne traite que les appels ODBC; il transmet les relevés SQL au moteur de base de données pour le traitement. Par exemple, les pilotes Oracle sont des pilotes basés sur DBMS parce qu’Oracle dispose d’un moteur de base de données autonome que le conducteur utilise. L’endroit où se trouve le moteur de base de données est sans importance. Il peut résider sur la même machine que le conducteur ou une machine différente sur le réseau; il pourrait même être accessible par une passerelle.  
  
 L’architecture du conducteur n’est généralement intéressante que pour les auteurs de pilotes; c’est-à-dire que l’architecture du conducteur ne fait généralement aucune différence dans l’application. Cependant, l’architecture peut influer sur la question de savoir si une application peut utiliser SQL spécifique à DBMS. Par exemple, Microsoft Access fournit un moteur de base de données autonome. Si un pilote Microsoft Access est basé sur DBMS - il accède aux données via ce moteur - l’application peut transmettre les relevés Microsoft Access-SQL au moteur pour le traitement.  
  
 Toutefois, si le pilote est basé sur des fichiers - c’est-à-dire qu’il contient un moteur propriétaire qui accède directement au fichier Microsoft® Access .mdb - toute tentative de transmettre directement les relevés SQL spécifiques à Microsoft Access au moteur est susceptible d’entraîner des erreurs de syntaxe. La raison en est que le moteur propriétaire est susceptible de mettre en œuvre seulement ODBC SQL.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Pilotes basés sur des fichiers](../../odbc/reference/file-based-drivers.md)  
  
-   [Pilotes basés sur le SGDB](../../odbc/reference/dbms-based-drivers.md)  
  
-   [Exemple de réseau](../../odbc/reference/network-example.md)  
  
-   [Autres architectures de pilote](../../odbc/reference/other-driver-architectures.md)
