---
title: Accès à la base de données réseau (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- network database access [ODBC]
- standardizing database access [ODBC], network
ms.assetid: f31dd938-e992-436b-b613-145c23973064
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2237c725d6fe3696d1f28d80c09f22183f718de8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295582"
---
# <a name="network-database-access"></a>Accès aux bases de données de réseau
L’accès à une base de données sur un réseau nécessite un certain nombre de composants, dont chacun est indépendant de l’interface de programmation et réside en dessous. Ces composants sont indiqués dans l’illustration suivante.  
  
 ![Composants pour accéder à une base de données sur un réseau](../../odbc/reference/media/pr04.gif "pr04")  
  
 Une autre description de chaque composant suit :  
  
-   **Interface de programmation** Comme décrit précédemment dans cette section, l’interface de programmation contient les appels effectués par l’application. Ces interfaces (SQL intégrées, modules SQL et interfaces de niveau d’appel) sont généralement spécifiques à chaque DBMS, bien qu’elles soient généralement basées sur une norme ANSI ou ISO.  
  
-   **Protocole de flux de données** Le protocole de flux de données décrit le flux de données transférés entre le DBMS et son client. Par exemple, le protocole peut exiger le premier byte pour décrire ce que contient le reste du flux : une déclaration SQL à exécuter, une valeur d’erreur retournée ou des données retournées. Le format du reste des données dans le flux dépendrait alors de ce drapeau. Par exemple, un flux d’erreurs peut contenir le drapeau, un code d’erreur integer à 2 ans, une longueur de message d’erreur integer à 2 ans et un message d’erreur.  
  
     Le protocole de flux de données est un protocole logique et est indépendant des protocoles utilisés par le réseau sous-jacent. Ainsi, un protocole unique de flux de données peut généralement être utilisé sur un certain nombre de réseaux différents. Les protocoles de flux de données sont généralement propriétaires et ont été optimisés pour fonctionner avec un DBMS particulier.  
  
-   **Mécanisme de communication interprocessus** Le mécanisme de communication interprocessus (IPC) est le processus par lequel un processus communique avec un autre. Les tuyaux nommés, les prises TCP/IP et les prises DECnet sont des exemples. Le choix du mécanisme IPC est limité par le système d’exploitation et le réseau utilisé.  
  
-   **Protocole réseau** Le protocole réseau est utilisé pour transporter le flux de données sur un réseau. On peut considérer la plomberie qui prend en charge les mécanismes du CIP utilisés pour mettre en œuvre le protocole de flux de données, ainsi que le soutien des opérations réseau de base telles que les transferts de fichiers et le partage d’impression. Les protocoles réseau incluent NetBEUI, TCP/IP, DECnet et SPX/IPX et sont spécifiques à chaque réseau.
