---
title: Positionné de traitement des instructions Update et Delete | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- SQL statements [ODBC], cursor library
- ODBC cursor library [ODBC], positioned update or delete
- cursor library [ODBC], statement processing
ms.assetid: 2975dd97-48e6-4d0a-a9c7-40759a7d94c8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d898fcc7d1b35230173afa0443219d59c54720ae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682743"
---
# <a name="processing-positioned-update-and-delete-statements"></a>Traitement des instructions de mise à jour et de suppression positionnées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Le prend en charge de bibliothèque de curseur positionné instructions update et delete en remplaçant le **WHERE CURRENT OF** clause dans ces instructions avec un **où** clause qui énumère les valeurs stockées dans son cache de chaque colonne dépendante. La bibliothèque de curseurs passe nouvellement construit **mise à jour** et **supprimer** instructions au pilote pour l’exécution. Pour les instructions de mise à jour positionnée, la bibliothèque de curseurs met à jour son cache à partir des valeurs dans les mémoires tampons d’ensemble de lignes et définit la valeur correspondante dans le tableau d’état de ligne à SQL_ROW_UPDATED. Pour les instructions delete positionnée, il définit la valeur correspondante dans le tableau d’état de ligne à SQL_ROW_DELETED.  
  
> [!CAUTION]  
>  Le **où** clause construit par la bibliothèque de curseurs pour identifier la ligne actuelle peut échouer pour identifier toutes les lignes, identifier une ligne différente ou identifier plusieurs lignes. Pour plus d’informations, consultez [construisant des instructions recherché](../../../odbc/reference/appendixes/constructing-searched-statements.md), plus loin dans cette annexe.  
  
 Positionné de mise à jour et supprimer les instructions sont soumis aux restrictions suivantes :  
  
-   Positionné update et delete instructions peuvent être utilisées uniquement dans les cas suivants : quand un **sélectionnez** l’instruction produit le jeu de résultats ; lorsque la **sélectionnez** instruction ne contenait pas d’une jointure, une  **UNION** clause, ou un **GROUP BY** clause ; et lorsque toutes les colonnes qui a utilisé un alias ou une expression dans la liste select n’étaient pas liés avec **SQLBindCol**.  
  
-   Si une application prépare une mise à jour positionnée ou une instruction delete, il doit le faire après l’appel **SQLFetch** ou **SQLFetchScroll**. Bien que la bibliothèque de curseurs soumet l’instruction au pilote pour la préparation, il ferme l’instruction et l’exécute directement lorsque l’application appelle **SQLExecute**.  
  
-   Si le pilote prend en charge qu’une seule instruction active, les extractions de bibliothèque de curseurs le reste du résultat défini et réextrait ensuite l’ensemble de lignes en cours à partir de son cache avant d’exécuter un positionnées mettre à jour ou supprimer l’instruction. Si l’application appelle ensuite une fonction qui retourne des métadonnées dans un jeu de résultats (par exemple, **SQLNumResultCols** ou **SQLDescribeCol**), la bibliothèque de curseurs retourne une erreur.  
  
-   Si une mise à jour positionnée ou une instruction delete est effectuée sur une colonne d’une table qui comprend une colonne d’horodatage est mis à jour automatiquement chaque fois qu’une mise à jour est effectuée, toutes les mises à jour positionnées ou des instructions delete échoue si la colonne timestamp est lié. Cela se produit car le jour ou de supprimer la détection de l’instruction qui crée la bibliothèque de curseurs n’identifie pas avec précision la ligne à mettre à jour. La valeur dans l’instruction de recherche pour la colonne timestamp n’a pas correspondra à la valeur mise à jour automatiquement de la colonne timestamp.
