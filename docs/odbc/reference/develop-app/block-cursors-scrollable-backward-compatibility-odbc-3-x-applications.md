---
title: Bloc et compatibilité de curseurs avec défilement pour ODBC 3.x | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- SQLExtendedFetch function [ODBC], block cursors
- cursors [ODBC], compatibility issues
- SQLFetchScroll function [ODBC], block cursors
ms.assetid: 82f6cf68-cfde-4417-9788-d6382ca14bf8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0bc45169a3c5eee2e23f581a66d5232c22e89b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199263"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>Curseurs de bloc, curseurs avec défilement et compatibilité descendante pour les applications ODBC 3.x
L’existence des deux **SQLFetchScroll** et **SQLExtendedFetch** représente la première clear Fractionner dans ODBC entre l’Interface API (Application Programming), qui est l’ensemble de fonctions le les appels de l’application et l’Interface de fournisseur de Service (SPI), qui est l’ensemble de fonctions le pilote implémente. Cette distinction est nécessaire pour équilibrer le fait dans ODBC 3. *x*, qui utilise **SQLFetchScroll**, pour s’aligner avec les normes et être compatible avec ODBC 2. *x*, qui utilise **SQLExtendedFetch**.  
  
 Le 3 ODBC *.x* API, qui est l’ensemble de l’application appelle les fonctions, inclut **SQLFetchScroll** et les attributs d’instruction. Le 3 ODBC *.x* SPI, qui est l’ensemble de fonctions, le pilote implémente, inclut **SQLFetchScroll**, **SQLExtendedFetch**et les attributs d’instruction. Comme ODBC n’applique pas formellement cette distinction entre l’API et le SPI, il est possible pour ODBC 3 *.x* applications d’appeler **SQLExtendedFetch** et les attributs d’instruction. Toutefois, il n’existe aucune raison pour ODBC 3 *.x* applications pour ce faire. Pour plus d’informations sur les API et SPI, reportez-vous à l’introduction [Architecture ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Pour plus d’informations sur la façon la ODBC 3. *x* Gestionnaire de pilotes mappe des appels à ODBC 2. *x* et ODBC 3. *x* des pilotes et les fonctions et l’instruction attributs un ODBC 3. *x* pilote doit implémenter pour le bloc et de curseurs avec défilement, consultez [ce que le pilote fait](../../../odbc/reference/appendixes/what-the-driver-does.md) dans g : annexe Instructions de pilote pour la compatibilité descendante.  
  
 Le tableau suivant récapitule les fonctions d’attributs et d’instruction une ODBC 3. *x* application doit utiliser avec bloc et de curseurs avec défilement. Il répertorie également les modifications entre ODBC 2. *x* et ODBC 3. *x* dans cette zone que ODBC 3. *x* applications doivent connaître pour être compatible avec ODBC 2. *x* pilotes.  
  
|Fonction ou<br /><br /> attribut d'instruction|Commentaires|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Pointe vers le signet à utiliser avec **SQLFetchScroll**.<br /><br /> Lorsqu’une application définit cela dans un ODBC 2. *x* pilote, il doit pointer vers un signet de longueur fixe.|  
|SQL_ATTR_ROW_STATUS_PTR|Pointe vers le tableau d’état des lignes remplies par **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, et **SQLSetPos**.<br /><br /> Si une application définit cela dans un ODBC 2. *x* pilote et les appels **SQLBulkOperation** avec un *opération* de SQL_ADD avant d’appeler **SQLFetchScroll**,  **SQLFetch**, ou **SQLExtendedFetch**, SQLSTATE HY011 (attribut ne peut pas être défini maintenant) est retournée.<br /><br /> Lorsqu’une application appelle **SQLFetch** dans un ODBC 2. *x* pilote, **SQLFetch** est mappé à **SQLExtendedFetch** et par conséquent retourne les valeurs dans ce tableau.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Pointe vers la mémoire tampon dans laquelle **SQLFetch** et **SQLFetchScroll** retourner le nombre de lignes extraites.<br /><br /> Lorsqu’une application appelle **SQLFetch** dans un ODBC 2. *x* pilote, **SQLFetch** est mappé à **SQLExtendedFetch** et par conséquent retourne une valeur dans cette mémoire tampon.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Définit la taille de l’ensemble de lignes.<br /><br /> Si une application appelle **SQLBulkOperations** avec un *opération* de SQL_ADD dans une API ODBC 2. *x* pilote, SQL_ROWSET_SIZE sera utilisé pour l’appel, pas SQL_ATTR_ROW_ARRAY_SIZE, car l’appel est mappé à **SQLSetPos** avec un *opération* de SQL_ADD, qui utilise SQL_ROWSET_SIZE.<br /><br /> Appel **SQLSetPos** avec un *opération* de SQL_ADD ou **SQLExtendedFetch** dans une application ODBC 2. *x* pilote utilise SQL_ROWSET_SIZE.<br /><br /> Appel **SQLFetch** ou **SQLFetchScroll** dans une application ODBC 2. *x* pilote utilise SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLBulkOperations**|Effectue des opérations d’insertion et de signet. Lorsque **SQLBulkOperations** avec un *opération* de SQL_ADD est appelée dans une API ODBC 2. *x* pilote, il est mappé à **SQLSetPos** avec un *opération* de SQL_ADD. Détails d’implémentation sont les suivantes :<br /><br /> -Lorsque vous travaillez avec un ODBC 2. *x* pilote, une application doit utiliser uniquement le ARD alloué implicitement associé à la *au paramètre StatementHandle*; il ne peut pas allouer un autre ARD pour ajouter des lignes, car les opérations de descripteurs sont non pris en charge dans une API ODBC 2. *x* pilote. Une application doit utiliser **SQLBindCol** à lier à la ARD, ne pas **SQLSetDescField** ou **SQLSetDescRec**.<br />-Lorsque vous appelez un ODBC 3. *x* pilote, une application peut appeler **SQLBulkOperations** avec un *opération* de SQL_ADD avant d’appeler **SQLFetch** ou **SQLFetchScroll**. Lors de l’appel d’une API ODBC 2. *x* pilote, une application doit appeler **SQLFetchScroll** avant d’appeler **SQLBulkOperations** avec une opération de SQL_ADD.|  
|**SQLFetch**|Retourne l’ensemble de lignes suivant. Détails d’implémentation sont les suivantes :<br /><br /> -Lorsqu’une application appelle **SQLFetch** dans un ODBC 2. *x* pilote, il est mappé à **SQLExtendedFetch**.<br />-Lorsqu’une application appelle **SQLFetch** dans un ODBC 3. *x* pilote, elle retourne le nombre de lignes spécifié avec l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLFetchScroll**|Retourne l’ensemble de lignes spécifié. Détails d’implémentation sont les suivantes :<br /><br /> -Lorsqu’une application appelle **SQLFetchScroll** dans un ODBC 2. *x* pilote, elle retourne 01 s 01 SQLSTATE (erreur de ligne) avant chaque erreur qui s’applique à une seule ligne. Pour cela, uniquement parce que le ODBC 3 *.x* Gestionnaire de pilotes le mappe à **SQLExtendedFetch** et **SQLExtendedFetch** retourne ce SQLSTATE. Lorsqu’une application appelle **SQLFetchScroll** dans un ODBC 3. *x* pilote, elle ne retourne jamais 01 s 01 SQLSTATE (erreur de ligne).<br />-Lorsqu’une application appelle **SQLFetchScroll** dans un ODBC 2. *x* pilote avec *FetchOrientation* SQL_FETCH_BOOKMARK, la valeur la *FetchOffset* argument doit être défini sur 0. SQLSTATE HYC00 (fonctionnalité facultative non implémentée) est retournée si l’extraction en fonction du décalage de signet est tentée avec une API ODBC 2. *x* pilote.|  
  
> [!NOTE]  
>  ODBC 3. *x* applications ne doivent pas utiliser **SQLExtendedFetch** ou l’attribut d’instruction SQL_ROWSET_SIZE. Au lieu de cela, ils doivent utiliser **SQLFetchScroll** et l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE. ODBC 3. *x* applications ne doivent pas utiliser **SQLSetPos** avec un *opération* de SQL_ADD mais vous devez utiliser **SQLBulkOperations** avec un *Opération* de SQL_ADD.
