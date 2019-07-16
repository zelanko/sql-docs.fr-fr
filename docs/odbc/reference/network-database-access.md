---
title: Accès de base de données réseau | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f8eaebca02ef3987e3613b5dd896e0f7c130086
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938032"
---
# <a name="network-database-access"></a>Accès aux bases de données de réseau
L’accès à une base de données sur un réseau nécessite un certain nombre de composants, chacun d’eux est indépendante d’et se trouve en dessous de l’interface de programmation. Ces composants sont affichés dans l’illustration suivante.  
  
 ![Composants pour accéder à une base de données sur un réseau](../../odbc/reference/media/pr04.gif "pr04")  
  
 Une description détaillée de chaque composant suit :  
  
-   **Interface de programmation** comme décrit précédemment dans cette section, l’interface de programmation contient les appels effectués par l’application. Ces interfaces (embedded SQL, SQL modules et les interfaces de niveau d’appel) sont généralement propres à chaque SGBD, même si elles sont généralement basées sur une norme ANSI ou ISO.  
  
-   **Protocole de données Stream** le protocole de flux de données décrit le flux de données transférées entre le SGBD et son client. Par exemple, le protocole peut nécessiter le premier octet pour décrire ce que contient le reste du flux : une instruction SQL pour être exécutée, une valeur d’erreur retourné, ou a retourné des données. Le format du reste des données dans le flux de données dépendent ensuite cet indicateur. Par exemple, un flux d’erreur peut contenir l’indicateur, un code d’erreur entier de 2 octets, une longueur de message d’erreur entier de 2 octets et un message d’erreur.  
  
     Le protocole de flux de données est un protocole logique et est indépendant des protocoles utilisés par le réseau sous-jacent. Par conséquent, un protocole de flux de données unique peut généralement être utilisé sur un nombre de différents réseaux. Protocoles de flux de données sont généralement propriétaires et ont été optimisées pour fonctionner avec un SGBD particulier.  
  
-   **Mécanisme de Communication d’interprocessus** le mécanisme de communication interprocessus (IPC) est le processus par lequel un processus communique avec un autre. Exemples incluent des canaux nommés, les sockets TCP/IP et les sockets DECnet. Le choix du mécanisme IPC est limité par le système d’exploitation et le réseau utilisé.  
  
-   **Protocole réseau** le protocole de réseau est utilisé pour transporter le flux de données sur un réseau. Il peut être considéré comme la plomberie que prend en charge les mécanismes IPC permettant d’implémenter les données flux de protocole, mais aussi en charge des opérations de réseau de base telles que les transferts de fichiers et partage d’impression. Protocoles réseau incluent NetBEUI, TCP/IP, DECnet et SPX/IPX et sont spécifiques à chaque réseau.
