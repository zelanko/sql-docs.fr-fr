---
title: Interfaces de niveau d’appel (en anglais) Microsoft Docs
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
ms.openlocfilehash: 4288a278f745d533c92d3d45892753ef1a74c2b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306540"
---
# <a name="call-level-interfaces"></a>Interfaces de niveau d’appel
La technique finale pour envoyer des relevés SQL au DBMS est par le biais d’une interface de niveau d’appel (CLI). Une interface au niveau des appels fournit une bibliothèque de fonctions DBMS qui peuvent être appelées par le programme d’application. Ainsi, au lieu d’essayer de mélanger SQL avec un autre langage de programmation, une interface de niveau d’appel est similaire aux bibliothèques de routine que la plupart des programmeurs sont habitués à utiliser, comme la chaîne, I/O, ou les bibliothèques de mathématiques dans C. Notez que les DBMS qui prennent en charge sqL intégrée ont déjà une interface de niveau d’appel, les appels à qui sont générés par le précompaler. Toutefois, ces appels sont sans papiers et peuvent être modifiés sans préavis.  
  
 Les interfaces de niveau d’appel sont couramment utilisées dans les architectures client/serveur, dans lesquelles le programme d’application (le client) réside sur un ordinateur et le DBMS (le serveur) se trouve sur un autre ordinateur. L’application appelle les fonctions CLI sur le système local, et ces appels sont envoyés à travers le réseau à la DBMS pour le traitement.  
  
 Une interface de niveau d’appel est similaire à SQL dynamique, en ce que les déclarations SQL sont transmises à la DBMS pour le traitement au moment de l’exécution, mais elle diffère de SQL intégrée dans son ensemble en ce qu’il n’y a pas de déclarations SQL intégrées et aucun précompiler n’est nécessaire.  
  
 L’utilisation d’une interface de niveau d’appel comporte généralement les étapes suivantes :  
  
1.  L’application appelle une fonction CLI pour se connecter à la DBMS.  
  
2.  L’application construit une déclaration SQL et le place dans un tampon. Il appelle ensuite une ou plusieurs fonctions CLI pour envoyer la déclaration à la DBMS pour la préparation et l’exécution.  
  
3.  Si l’instruction est une déclaration SELECT, l’application appelle une fonction CLI pour retourner les résultats dans les tampons d’application. Typiquement, cette fonction renvoie une rangée ou une colonne de données à la fois.  
  
4.  L’application appelle une fonction CLI pour se déconnecter de la DBMS.
