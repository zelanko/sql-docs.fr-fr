---
title: Niveau d’appel Interfaces | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6c37084ad91a931c4479ecf826c5cb554765412
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135672"
---
# <a name="call-level-interfaces"></a>Interfaces de niveau d’appel
La dernière technique pour l’envoi d’instructions SQL au SGBD est via une interface de niveau d’appel (CLI). Une interface de niveau d’appel fournit une bibliothèque de fonctions de SGBD qui peut être appelée par le programme d’application. Par conséquent, au lieu de tenter de fusion SQL avec un autre langage de programmation, une interface de niveau d’appel est similaire aux bibliothèques routines la plupart des programmeurs sont habitués à utiliser, telles que la chaîne, d’e/s ou des bibliothèques de mathématiques dans C. Notez ce SGBD qui prennent en charge embedded SQL vous disposez déjà d’une interface de niveau d’appel, les appels à laquelle sont générés par le précompilateur. Toutefois, ces appels sont non documentées et l’objet de modifications sans préavis.  
  
 Interfaces de niveau d’appel sont couramment utilisés dans les architectures client/serveur, dans lequel le programme d’application (le client) réside sur un ordinateur et le SGBD (serveur) se trouve sur un autre ordinateur. L’application appelle les fonctions de l’interface CLI sur le système local, et ces appels sont envoyés sur le réseau au SGBD pour le traitement.  
  
 Une interface de niveau d’appel est similaire à SQL dynamique, car les instructions SQL sont passées au SGBD pour le traitement en cours d’exécution, mais il diffère d’embedded SQL dans sa globalité car il n’existe aucune des instructions SQL incorporées et aucun précompilateur n’est requis.  
  
 À l’aide d’une interface de niveau d’appel généralement implique les étapes suivantes :  
  
1.  L’application appelle une fonction de l’interface CLI pour vous connecter au SGBD.  
  
2.  L’application génère une instruction SQL et le place dans une mémoire tampon. Il appelle ensuite une ou plusieurs fonctions CLI pour l’envoi de l’instruction au SGBD pour la préparation et l’exécution.  
  
3.  Si l’instruction est une instruction SELECT, l’application appelle une fonction de l’interface CLI pour retourner les résultats dans les tampons de l’application. En règle générale, cette fonction retourne une ligne ou une colonne de données à la fois.  
  
4.  L’application appelle une fonction de l’interface CLI pour vous déconnecter de SGBD.
