---
title: 'Annexe F : Bibliothèque ODBC Cursor (fr) Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec7982150bfa805c7093ab445400ef5ad1ee070c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292429"
---
# <a name="appendix-f-odbc-cursor-library"></a>Annexe F : Bibliothèque de curseurs ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 La bibliothèque de curseurs ODBC (Odbccr32.dll) prend en charge les curseurs défilements de bloc pour tout pilote qui respecte le niveau de conformité API de niveau 1 et peut être redistribué par les développeurs avec leurs applications ou pilotes. La bibliothèque de curseurs prend également en charge la mise à jour positionnée et supprime les instructions pour les ensembles de résultats générés par les relevés **SELECT.** Bien qu’elle ne supporte que des curseurs statiques et avant-seulement, la bibliothèque de curseurs répond aux besoins de nombreuses applications. En outre, il peut fournir de bonnes performances, en particulier pour les ensembles de résultats de petite et moyenne taille, et pour les applications qui n’ont pas un bon support curseur.  
  
 La bibliothèque de curseurs est une bibliothèque dynamique qui se trouve entre le Driver Manager et le conducteur. Lorsqu’une application appelle une fonction, le gestionnaire de pilote appelle la fonction dans la bibliothèque du curseur, qui exécute la fonction ou l’appelle dans le pilote spécifié. Pour une connexion donnée, une application précise si la bibliothèque de curseurs est toujours utilisée, utilisée si le conducteur ne prend pas en charge les curseurs défilementables, ou n’a jamais été utilisé.  
  
 La bibliothèque de curseurs apparaît comme un conducteur au gestionnaire de conducteur. Si la bibliothèque de curseurs se trouve entre le gestionnaire de conducteur et un conducteur ODBC *2.x,* la bibliothèque de curseur apparaît comme un conducteur ODBC *2.x.* Si la bibliothèque de curseurs se trouve entre le gestionnaire de conducteur et un conducteur ODBC *3.x,* la bibliothèque de curseur apparaît comme un conducteur ODBC *3.x.* Le comportement exposé par la bibliothèque de curseurs dépend de la version du conducteur avec laquelle elle travaille, à l’exception des décalages contraignants, qui est pris en charge pour les conducteurs ODBC *2.x* et ODBC *3.x.*  
  
 Pour mettre en œuvre des curseurs de blocs dans **SQLFetch** et **SQLFetchScroll**, la bibliothèque de curseurs appelle à plusieurs reprises **SQLFetch** dans le conducteur. Pour implémenter le défilement, il cache les données qu’il a récupérées dans la mémoire et dans les fichiers disque. Lorsqu’une demande demande un nouveau ramset, la bibliothèque de curseurs la récupère au besoin auprès du conducteur ou du cache.  
  
 Pour implémenter les instructions de mise à jour et de suppression positionnées, la bibliothèque de curseurs construit une déclaration **UPDATE** ou **DELETE** avec une clause **WHERE** qui spécifie la valeur mise en cache de chaque colonne liée dans la rangée. Lorsqu’elle exécute une instruction de mise à jour positionnée, la bibliothèque de curseurs met à jour son cache à partir des valeurs des tampons encastrés.  
  
 Pour plus d’informations sur la bibliothèque de curseurs de l’ODBC, consultez les sections suivantes de cette annexe :  
  
-   [Utilisation de la bibliothèque de curseurs ODBC](../../../odbc/reference/appendixes/using-the-odbc-cursor-library.md)  
  
-   [Exécution d’instructions de mise à jour et de suppression positionnées](../../../odbc/reference/appendixes/executing-positioned-update-and-delete-statements.md)  
  
-   [Exemple de code de la bibliothèque de curseurs](../../../odbc/reference/appendixes/cursor-library-code-example.md)  
  
-   [Remarques relatives à l’implémentation](../../../odbc/reference/appendixes/implementation-notes.md)  
  
-   [Codes d’erreur de la bibliothèque de curseurs ODBC](../../../odbc/reference/appendixes/odbc-cursor-library-error-codes.md)
