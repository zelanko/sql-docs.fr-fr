---
title: 'Annexe F : Bibliothèque de curseurs ODBC | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- cursor library [ODBC]
ms.assetid: a03084df-4e48-48ef-917d-4a3fae48a605
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c27845976651b0d68b91b6269a21d1cae3518df8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267801"
---
# <a name="appendix-f-odbc-cursor-library"></a>Annexe F : Bibliothèque de curseurs ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 La bibliothèque de curseurs ODBC (Odbccr32.dll) prend en charge des curseurs avec défilement de bloc pour n’importe quel pilote est conforme avec le niveau de conformité de niveau 1 API et peut être redistribuée par les développeurs avec leurs applications ou des pilotes. La bibliothèque de curseurs prend également en charge positionnée instructions update et delete pour les jeux de résultats générés par **sélectionnez** instructions. Bien qu’il prend en charge uniquement curseurs statiques et avant uniquement, la bibliothèque de curseurs répond aux besoins de nombreuses applications. En outre, il offre de bonnes performances, en particulier pour les jeux de résultats de taille petite à moyenne taille et pour les applications qui n’ont pas de prise en charge du curseur bon.  
  
 La bibliothèque de curseurs est une bibliothèque de liens dynamiques (DLL) qui réside entre le Gestionnaire de pilotes et le pilote. Lorsqu’une application appelle une fonction, le Gestionnaire de pilotes appelle la fonction dans la bibliothèque de curseurs, qui exécute la fonction ou appelle dans le pilote spécifié. Pour une connexion donnée, une application spécifie la bibliothèque de curseurs est toujours utilisée, utilisée si le pilote ne prend pas en charge les curseurs avec défilement ou jamais utilisée.  
  
 La bibliothèque de curseurs s’affiche en tant que pilote pour le Gestionnaire de pilotes. Si la bibliothèque de curseurs réside entre le Gestionnaire de pilotes et une API ODBC 2. *x* pilote, la bibliothèque de curseurs apparaît sous la forme d’une API ODBC 2. *x* pilote. Si la bibliothèque de curseurs réside entre le Gestionnaire de pilotes et un ODBC 3 *.x* pilote, la bibliothèque de curseurs apparaît sous la forme d’un ODBC 3 *.x* pilote. Le comportement exposé par la bibliothèque de curseurs dépend de la version du pilote que fonctionne avec, à l’exception des décalages de liaison, qui est pris en charge pour les deux ODBC 2. *x* et ODBC 3. *x* pilotes.  
  
 Pour implémenter des curseurs de bloc dans **SQLFetch** et **SQLFetchScroll**, la bibliothèque de curseurs appelle à plusieurs reprises **SQLFetch** dans le pilote. Pour implémenter le défilement, il met en cache les données qu’il a récupéré dans la mémoire et dans les fichiers de disque. Lorsqu’une application demande un nouvel ensemble de lignes, la bibliothèque de curseurs le récupère en fonction des besoins dans le pilote ou le cache.  
  
 Pour implémenter la mise à jour positionnée et supprimer des instructions, la bibliothèque de curseurs construit un **mettre à jour** ou **supprimer** instruction avec un **où** clause qui spécifie la mise en cache valeur de chaque colonne dépendante dans la ligne. Lorsqu’il exécute une instruction de mise à jour positionnée, la bibliothèque de curseurs met à jour son cache à partir des valeurs dans les mémoires tampons d’ensemble de lignes.  
  
 Pour plus d’informations sur la bibliothèque de curseurs ODBC, consultez les sections suivantes de cette annexe :  
  
-   [Utilisation de la bibliothèque de curseurs ODBC](../../../odbc/reference/appendixes/using-the-odbc-cursor-library.md)  
  
-   [Exécution d’instructions de mise à jour et de suppression positionnées](../../../odbc/reference/appendixes/executing-positioned-update-and-delete-statements.md)  
  
-   [Exemple de code de la bibliothèque de curseurs](../../../odbc/reference/appendixes/cursor-library-code-example.md)  
  
-   [Remarques sur l’implémentation](../../../odbc/reference/appendixes/implementation-notes.md)  
  
-   [Codes d’erreur de la bibliothèque de curseurs ODBC](../../../odbc/reference/appendixes/odbc-cursor-library-error-codes.md)
