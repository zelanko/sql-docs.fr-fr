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
manager: craigg
ms.openlocfilehash: a8e49b89d233880652f4b19879ff8e658bc4abe1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628397"
---
# <a name="driver-architecture"></a>Architecture des pilotes
Architecture du pilote se divise en deux catégories, selon les instructions SQL de processus logiciel :  
  
-   **Pilotes basés sur le fichier** le pilote accède directement aux données physiques. Dans ce cas, le pilote fonctionne comme pilote et de source de données ; Autrement dit, il traite les appels ODBC et des instructions SQL. Par exemple, dBASE pilotes sont basés sur fichier dBASE ne fournissant pas de qu'un moteur de base de données autonome le pilote peut utiliser. Il est important de noter que les développeurs de pilotes basés sur le fichier doivent écrire leurs propres moteurs de base de données.  
  
-   **Pilotes basés sur SGBD** le pilote accède aux données physiques via un moteur de base de données distincte. Dans ce cas le pilote traite uniquement les appels ODBC ; Il passe les instructions SQL au moteur de base de données pour traitement. Par exemple, Oracle pilotes sont basés sur SGBD, car Oracle a un moteur de base de données autonome qu'utilise le pilote. Où se trouve le moteur de base de données est immatériel. Il peut résider sur le même ordinateur que le pilote ou un autre ordinateur sur le réseau ; Il peut même être accessible via une passerelle.  
  
 Architecture du pilote est généralement utile pour les rédacteurs de pilotes ; Autrement dit, architecture de pilote généralement indifféremment à l’application. Toutefois, l’architecture peut affecter si une application peut utiliser SQL de SGBD spécifiques. Par exemple, Microsoft Access fournit un moteur de base de données autonome. Si un pilote Microsoft Access est basé sur des SGBD, il accède aux données via ce moteur, l’application peut passer les instructions SQL à Microsoft Access pour le moteur pour traitement.  
  
 Toutefois, si le pilote est basé sur fichier, autrement dit, il contient un moteur de propriétaire qui accède directement au fichier .mdb de Microsoft® Access, toutes les tentatives de transmettre les instructions spécifiques à Microsoft Access SQL au moteur sont susceptibles d’entraîner des erreurs de syntaxe. La raison est que le moteur de propriétaire est susceptible d’implémenter uniquement ODBC SQL.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Pilotes basés sur des fichiers](../../odbc/reference/file-based-drivers.md)  
  
-   [Pilotes basés sur le SGDB](../../odbc/reference/dbms-based-drivers.md)  
  
-   [Exemple de réseau](../../odbc/reference/network-example.md)  
  
-   [Autres architectures de pilote](../../odbc/reference/other-driver-architectures.md)
