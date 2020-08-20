---
description: Curseurs de bloc, curseurs avec défilement et compatibilité descendante pour les applications ODBC 3.x
title: Compatibilité des curseurs de bloc et de défilement pour ODBC 3. x | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96645f91d52f4141aacf4f2e171ef809a639f73c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476831"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>Curseurs de bloc, curseurs avec défilement et compatibilité descendante pour les applications ODBC 3.x
L’existence de **SQLFetchScroll** et **SQLExtendedFetch** représente le premier fractionnement clair dans ODBC entre l’interface de programmation d’applications (API), qui est l’ensemble des fonctions que l’application appelle, et l’interface de fournisseur de services (SPI), qui est l’ensemble de fonctions implémentées par le pilote. Ce fractionnement est requis pour équilibrer l’exigence dans ODBC *3. x*, qui utilise **SQLFetchScroll**, pour aligner les normes et être compatible avec ODBC *2. x*, qui utilise **SQLExtendedFetch**.  
  
 L’API ODBC *3. x* , qui est l’ensemble des fonctions appelées par l’application, comprend **SQLFetchScroll** et les attributs d’instruction associés. Le SPI ODBC *3. x* , qui est l’ensemble des fonctions implémentées par le pilote, comprend **SQLFetchScroll**, **SQLExtendedFetch**et les attributs d’instruction associés. Dans la mesure où ODBC n’impose pas cette séparation entre l’API et le SPI, il est possible pour les applications ODBC *3. x* d’appeler **SQLExtendedFetch** et les attributs d’instruction associés. Toutefois, il n’y a aucune raison pour que les applications ODBC *3. x* le fassent. Pour plus d’informations sur les API et les SPI, consultez Introduction à [ODBC architecture](../../../odbc/reference/odbc-architecture.md).  
  
 Pour plus d’informations sur la façon dont le gestionnaire de pilotes ODBC *3. x* mappe les appels aux pilotes ODBC *2. x* et ODBC *3. x* , ainsi que les fonctions et attributs d’instruction qu’un pilote ODBC *3. x* doit implémenter pour les curseurs de bloc et de défilement, voir [ce que fait le pilote](../../../odbc/reference/appendixes/what-the-driver-does.md) dans annexe G : instructions relatives aux pilotes pour la compatibilité descendante.  
  
 Le tableau suivant récapitule les fonctions et attributs d’instruction qu’une application ODBC *3. x* doit utiliser avec les curseurs de bloc et de défilement. Il répertorie également les modifications entre ODBC *2. x* et ODBC *3. x* dans ce domaine que les applications ODBC *3. x* doivent connaître pour être compatibles avec les pilotes ODBC *2. x* .  
  
|Function ou<br /><br /> attribut d'instruction|Commentaires|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Pointe vers le signet à utiliser avec **SQLFetchScroll**.<br /><br /> Quand une application définit cette valeur dans un pilote ODBC *2. x* , elle doit pointer vers un signet de longueur fixe.|  
|SQL_ATTR_ROW_STATUS_PTR|Pointe vers le tableau d’état de ligne rempli par **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**et **SQLSetPos**.<br /><br /> Si une application définit cette valeur dans un pilote ODBC *2. x* et appelle **SQLBulkOperation** avec une *opération* de SQL_ADD avant d’appeler **SQLFETCHSCROLL**, **SQLFetch**ou **SQLExtendedFetch**, SQLSTATE HY011 (l’attribut ne peut pas être défini maintenant) est retourné.<br /><br /> Quand une application appelle **SQLFetch** dans un pilote ODBC *2. x* , **SQLFetch** est mappé à **SQLExtendedFetch** et retourne donc des valeurs dans ce tableau.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Pointe vers la mémoire tampon dans laquelle **SQLFetch** et **SQLFetchScroll** retournent le nombre de lignes extraites.<br /><br /> Quand une application appelle **SQLFetch** dans un pilote ODBC *2. x* , **SQLFetch** est mappé à **SQLExtendedFetch** et retourne donc une valeur dans cette mémoire tampon.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Définit la taille de l’ensemble de lignes.<br /><br /> Si une application appelle **SQLBulkOperations** avec une *opération* de SQL_ADD dans un pilote ODBC *2. x* , SQL_ROWSET_SIZE sera utilisé pour l’appel, pas SQL_ATTR_ROW_ARRAY_SIZE, car l’appel est mappé à **SQLSetPos** avec une *opération* de SQL_ADD, qui utilise SQL_ROWSET_SIZE.<br /><br /> L’appel de **SQLSetPos** avec une *opération* de SQL_ADD ou **SQLExtendedFetch** dans un pilote ODBC *2. x* utilise SQL_ROWSET_SIZE.<br /><br /> L’appel de **SQLFetch** ou **SQLFetchScroll** dans un pilote ODBC *2. x* utilise SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLBulkOperations**|Exécute les opérations d’insertion et de signet. Lorsque **SQLBulkOperations** avec une *opération* de SQL_ADD est appelé dans un pilote ODBC *2. x* , il est mappé à **SQLSetPos** avec une *opération* de SQL_ADD. Voici les détails de l’implémentation :<br /><br /> -Lorsque vous utilisez un pilote ODBC *2. x* , une application doit utiliser uniquement les ARD alloués implicitement associés à *StatementHandle*. il ne peut pas allouer un autre ARD pour l’ajout de lignes, car les opérations de descripteur explicites ne sont pas prises en charge dans un pilote ODBC *2. x* . Une application doit utiliser **SQLBindCol** pour établir une liaison avec ARD, et non **SQLSetDescField** ou **SQLSetDescRec**.<br />-Lors de l’appel d’un pilote ODBC *3. x* , une application peut appeler **SQLBulkOperations** avec une *opération* de SQL_ADD avant d’appeler **SQLFetch** ou **SQLFetchScroll**. Lors de l’appel d’un pilote ODBC *2. x* , une application doit appeler **SQLFetchScroll** avant d’appeler **SQLBulkOperations** avec une opération de SQL_ADD.|  
|**SQLFetch**|Retourne l’ensemble de lignes suivant. Voici les détails de l’implémentation :<br /><br /> -Quand une application appelle **SQLFetch** dans un pilote ODBC *2. x* , elle est mappée à **SQLExtendedFetch**.<br />-Quand une application appelle **SQLFetch** dans un pilote ODBC *3. x* , elle retourne le nombre de lignes spécifié avec l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLFetchScroll**|Retourne l’ensemble de lignes spécifié. Voici les détails de l’implémentation :<br /><br /> -Lorsqu’une application appelle **SQLFetchScroll** dans un pilote ODBC *2. x* , elle retourne SQLState 01S01 (erreur dans la ligne) avant chaque erreur qui s’applique à une seule ligne. Cela est uniquement dû au fait que le gestionnaire de pilotes ODBC *3. x* mappe This à **SQLExtendedFetch** et **SQLExtendedFetch** retourne ce SQLSTATE. Quand une application appelle **SQLFetchScroll** dans un pilote ODBC *3. x* , elle ne retourne jamais SQLSTATE 01S01 (erreur dans la ligne).<br />-Quand une application appelle **SQLFetchScroll** dans un pilote ODBC *2. x* avec *FetchOrientation* défini sur SQL_FETCH_BOOKMARK, l’argument *FetchOffset* doit avoir la valeur 0. SQLSTATE HYC00 (fonctionnalité facultative non implémentée) est retournée si l’extraction de signet basée sur un décalage est tentée avec un pilote ODBC *2. x* .|  
  
> [!NOTE]  
>  Les applications ODBC *3. x* ne doivent pas utiliser **SQLExtendedFetch** ou l’attribut d’instruction SQL_ROWSET_SIZE. Au lieu de cela, ils doivent utiliser **SQLFetchScroll** et l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE. Les applications ODBC *3. x* ne doivent pas utiliser **SQLSetPos** avec une *opération* de SQL_ADD, mais doivent utiliser **SQLBulkOperations** avec une *opération* de SQL_ADD.
