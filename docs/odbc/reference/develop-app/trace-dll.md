---
title: Trace DLL - France Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- trace DLLs [ODBC]
- tracing options [ODBC], trace DLLs
ms.assetid: 5ab99bd3-cdc3-4e2c-8827-932d1fcb6e00
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8e1f9dc57415ad9865ca1b2ad02487b62a93f18f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298069"
---
# <a name="trace-dll"></a>DLL de traçage
Le DLL qui effectue le traçage est l’un des composants de base ODBC. La trace DLL est actuellement fournie comme un échantillon DLL dans le composant ODBC de la SDK Windows, et a été précédemment inclus le Microsoft Data Access Components (MDAC) SDK. Par conséquent, l’entrée de registre, l’interface, et le code d’échantillon pour le DLL trace sont disponibles. Ce DLL peut être remplacé par une trace DLL produite soit par un utilisateur d’ODBC ou un fournisseur tiers. Une trace personnalisée DLL doit être donné un nom différent de l’échantillon original trace DLL. Les DLL de trace doivent être installés dans le répertoire du système, ou ils ne se chargeront pas. Les chaînes de connexion ne seront pas transmises à la trace DLL par le Driver Manager.  
  
 La trace DLL retrace les arguments d’entrée, les arguments de sortie, les arguments différés, les codes de retour et les SQLSTATEs. Lorsque le traçage est activé, le Driver Manager appelle la trace DLL à deux points : une fois sur l’entrée de la fonction (avant validation de l’argument) et encore juste avant le retour de la fonction.  
  
 Lorsqu’une application appelle une fonction, le gestionnaire de conducteur appelle une fonction de trace dans la trace DLL avant d’appeler la fonction dans le pilote ou le traitement de l’appel lui-même. Chaque fonction ODBC a une fonction de trace correspondante (préfixée avec *Trace*) qui est identique à la fonction ODBC à l’exception du nom. Lorsque la fonction de trace est appelée, la trace DLL capture les arguments d’entrée et renvoie un code de retour. Étant donné que la trace DLL est appelée avant que le gestionnaire de conducteur valide les arguments, les appels de fonction invalides sont tracés, de sorte que les erreurs de transition de l’État et les arguments invalides sont enregistrés.  
  
 Après avoir appelé la fonction trace dans la trace DLL, le gestionnaire de conducteur appelle la fonction ODBC dans le conducteur. Il appelle alors **TraceReturn** dans la trace DLL. Cette fonction comporte deux arguments : la valeur retournée par la trace DLL pour la fonction de trace, et le code de retour retourné par le conducteur au gestionnaire de conducteur pour la fonction ODBC (ou la valeur retournée par le gestionnaire de conducteur lui-même si elle traitait la fonction). La fonction utilise la valeur retournée pour la fonction de trace pour manipuler les valeurs d’argument d’entrée capturées. Il écrit le code retourné pour la fonction ODBC au fichier journal (ou l’affiche dynamiquement, si cela est activé). Il dérefère l’argument de sortie pointeurs et enregistre les valeurs de l’argument de sortie.
