---
description: Interfaces de niveau d’appel
title: Interfaces de niveau appel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], CLI
- CLI [ODBC], using CLI
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], CLI
- call-level interface [ODBC], using call-level interface
ms.assetid: 42257bb6-0bf1-4533-a4ef-4a6dd2aecb18
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ad1e89f945dbb739c4c20103fc2330cbf4e562b5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448957"
---
# <a name="call-level-interfaces"></a>Interfaces de niveau d’appel
La dernière technique pour l’envoi d’instructions SQL au SGBD est d’utiliser une interface de niveau appel (CLI). Une interface au niveau de l’appel fournit une bibliothèque de fonctions SGBD qui peuvent être appelées par le programme d’application. Ainsi, au lieu d’essayer de fusionner SQL avec un autre langage de programmation, une interface au niveau de l’appel est similaire aux bibliothèques de routines que la plupart des programmeurs sont habitués à utiliser, comme les bibliothèques de chaînes, d’e/s ou mathématiques en C. Notez que les SGBD qui prennent en charge le SQL incorporé disposent déjà d’une interface de niveau appel, les appels Toutefois, ces appels ne sont pas documentés et peuvent faire l’objet de modifications sans préavis.  
  
 Les interfaces de niveau appel sont couramment utilisées dans les architectures client/serveur, dans lesquelles le programme d’application (le client) réside sur un ordinateur et le SGBD (le serveur) réside sur un autre ordinateur. L’application appelle les fonctions CLI sur le système local, et ces appels sont envoyés sur le réseau au SGBD pour traitement.  
  
 Une interface au niveau de l’appel est similaire au SQL dynamique, dans le cas où les instructions SQL sont passées au SGBD pour traitement au moment de l’exécution, mais diffère de SQL incorporé dans la mesure où il n’y a pas d’instructions SQL incorporées et qu’aucun précompilation n’est nécessaire.  
  
 L’utilisation d’une interface au niveau de l’appel implique généralement les étapes suivantes :  
  
1.  L’application appelle une fonction CLI pour se connecter au SGBD.  
  
2.  L’application génère une instruction SQL et la place dans une mémoire tampon. Il appelle ensuite une ou plusieurs fonctions CLI pour envoyer l’instruction au SGBD pour la préparation et l’exécution.  
  
3.  Si l’instruction est une instruction SELECT, l’application appelle une fonction CLI pour retourner les résultats dans les mémoires tampons d’application. En règle générale, cette fonction retourne une ligne ou une colonne de données à la fois.  
  
4.  L’application appelle une fonction CLI pour se déconnecter du SGBD.
