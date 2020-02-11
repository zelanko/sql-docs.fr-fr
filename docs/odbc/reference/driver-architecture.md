---
title: Architecture du pilote | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fd9bbb74d77a0b56b6b1f1aa5d8f1a6b5e97f5aa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915476"
---
# <a name="driver-architecture"></a>Architecture des pilotes
L’architecture du pilote se divise en deux catégories, selon le logiciel qui traite les instructions SQL :  
  
-   **Pilotes basés sur des fichiers** Le pilote accède directement aux données physiques. Dans ce cas, le pilote joue le rôle de pilote et de source de données ; autrement dit, il traite les appels ODBC et les instructions SQL. Par exemple, les pilotes dBASE sont des pilotes basés sur des fichiers, car dBASE ne fournit pas de moteur de base de données autonome que le pilote peut utiliser. Il est important de noter que les développeurs de pilotes basés sur des fichiers doivent écrire leurs propres moteurs de base de données.  
  
-   **Pilotes basés sur SGBD** Le pilote accède aux données physiques via un moteur de base de données distinct. Dans ce cas, le pilote traite uniquement les appels ODBC. Il transmet des instructions SQL au moteur de base de données pour le traitement. Par exemple, les pilotes Oracle sont des pilotes basés sur SGBD, car Oracle dispose d’un moteur de base de données autonome utilisé par le pilote. L’endroit où se trouve le moteur de base de données est inmaterial. Il peut résider sur le même ordinateur que le pilote ou sur un autre ordinateur sur le réseau. elle peut même être accessible par le biais d’une passerelle.  
  
 L’architecture du pilote est généralement intéressante uniquement pour les writers de pilote ; autrement dit, l’architecture du pilote ne fait généralement aucune différence avec l’application. Toutefois, l’architecture peut déterminer si une application peut utiliser SQL spécifique au SGBD. Par exemple, Microsoft Access fournit un moteur de base de données autonome. Si un pilote Microsoft Access est basé sur le SGBD, il accède aux données via ce moteur. l’application peut transmettre des instructions Microsoft Access-SQL au moteur pour traitement.  
  
 Toutefois, si le pilote est basé sur des fichiers, c’est-à-dire qu’il contient un moteur propriétaire qui accède directement au fichier Microsoft® Access. mdb, toute tentative de transmission d’instructions SQL spécifiques à Microsoft Access au moteur peut entraîner des erreurs de syntaxe. Cela est dû au fait que le moteur propriétaire est susceptible d’implémenter uniquement ODBC SQL.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Pilotes basés sur des fichiers](../../odbc/reference/file-based-drivers.md)  
  
-   [Pilotes basés sur le SGDB](../../odbc/reference/dbms-based-drivers.md)  
  
-   [Exemple de réseau](../../odbc/reference/network-example.md)  
  
-   [Autres architectures de pilote](../../odbc/reference/other-driver-architectures.md)
