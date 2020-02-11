---
title: Accès à la base de données réseau | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938032"
---
# <a name="network-database-access"></a>Accès aux bases de données de réseau
L’accès à une base de données sur un réseau nécessite un certain nombre de composants, chacun d’entre eux étant indépendant et résidant sous, il s’agit de l’interface de programmation. Ces composants sont présentés dans l’illustration suivante.  
  
 ![Composants pour accéder à une base de données sur un réseau](../../odbc/reference/media/pr04.gif "pr04")  
  
 Voici une description supplémentaire de chaque composant :  
  
-   **Interface de programmation** Comme décrit plus haut dans cette section, l’interface de programmation contient les appels effectués par l’application. Ces interfaces (Embedded SQL, modules SQL et interfaces de niveau d’appel) sont généralement spécifiques à chaque SGBD, bien qu’elles soient généralement basées sur une norme ANSI ou ISO.  
  
-   **Protocole de flux de données** Le protocole de flux de données décrit le flux de données transférées entre le SGBD et son client. Par exemple, le protocole peut nécessiter le premier octet pour décrire ce que contient le reste du flux : une instruction SQL à exécuter, une valeur d’erreur retournée ou des données retournées. Le format du reste des données dans le flux dépend ensuite de cet indicateur. Par exemple, un flux d’erreur peut contenir l’indicateur, un code d’erreur entier sur 2 octets, une longueur de message d’erreur sur un entier sur 2 octets et un message d’erreur.  
  
     Le protocole de flux de données est un protocole logique qui est indépendant des protocoles utilisés par le réseau sous-jacent. Par conséquent, un protocole de flux de données unique peut généralement être utilisé sur plusieurs réseaux différents. Les protocoles de flux de données sont généralement propriétaires et ont été optimisés pour fonctionner avec un SGBD particulier.  
  
-   **Mécanisme de communication entre processus** Le mécanisme de communication interprocessus (IPC) est le processus par lequel un processus communique avec un autre. Les exemples incluent des canaux nommés, des sockets TCP/IP et des sockets DECnet. Le choix du mécanisme IPC est imposé par le système d’exploitation et le réseau utilisés.  
  
-   **Protocole réseau** Le protocole réseau est utilisé pour transporter le flux de données sur un réseau. Il peut être considéré comme la plomberie qui prend en charge les mécanismes IPC utilisés pour implémenter le protocole de flux de données, ainsi que pour prendre en charge des opérations réseau de base telles que le transfert de fichiers et le partage d’imprimantes. Les protocoles réseau incluent NetBEUI, TCP/IP, DECnet et SPX/IPX et sont spécifiques à chaque réseau.
