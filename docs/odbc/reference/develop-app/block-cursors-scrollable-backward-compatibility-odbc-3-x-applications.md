---
title: Compatibilité des cursors de bloc et de défilement pour ODBC 3.x . Microsoft Docs
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
ms.openlocfilehash: c526eff6e19014c923f05ad91551a7d7c66f5294
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306340"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>Curseurs de bloc, curseurs avec défilement et compatibilité descendante pour les applications ODBC 3.x
L’existence de **SQLFetchScroll** et **SQLExtendedFetch** représente la première scission claire dans ODBC entre l’interface de programmation d’applications (API), qui est l’ensemble des fonctions des appels d’application, et l’interface fournisseur de services (SPI), qui est l’ensemble des fonctions que le conducteur met en œuvre. Cette scission est nécessaire pour équilibrer l’exigence dans ODBC *3.x*, qui utilise **SQLFetchScroll**, pour s’aligner avec les normes et être compatible avec ODBC *2.x*, qui utilise **SQLExtendedFetch**.  
  
 L’API ODBC *3.x,* qui est l’ensemble des fonctions des appels d’application, comprend **SQLFetchScroll** et les attributs de déclaration connexes. L’ODBC *3.x* SPI, qui est l’ensemble des fonctions que le conducteur met en œuvre, comprend **SQLFetchScroll**, **SQLExtendedFetch**, et les attributs de déclaration connexes. Étant donné qu’ODBC n’applique pas officiellement cette division entre l’API et le SPI, il est possible pour les applications ODBC *3.x* d’appeler **SQLExtendedFetch** et les attributs de déclaration connexes. Cependant, il n’y a aucune raison pour les applications ODBC *3.x* pour ce faire. Pour plus d’informations sur les API et les IFS, voir l’introduction à [ODBC Architecture](../../../odbc/reference/odbc-architecture.md).  
  
 Pour plus d’informations sur la façon dont le gestionnaire de conducteur ODBC *3.x* cartes appels à ODBC *2.x* et ODBC *3.x* pilotes, et quelles fonctions et l’instruction attribue un pilote ODBC *3.x* devrait mettre en œuvre pour les curseurs de bloc et défilement, voir [ce que le conducteur fait](../../../odbc/reference/appendixes/what-the-driver-does.md) dans Appendix G: Lignes directrices du conducteur pour la compatibilité vers l’arrière.  
  
 Le tableau suivant résume les fonctions et les énoncés qui attribuent une application ODBC *3.x* à utiliser avec des curseurs de blocs et défilements. Il répertorie également les changements entre ODBC *2.x* et ODBC *3.x* dans ce domaine que les applications ODBC *3.x* devraient être conscients d’être compatibles avec les pilotes ODBC *2.x.*  
  
|Fonction ou<br /><br /> attribut d'instruction|Commentaires|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Points au signet à utiliser avec **SQLFetchScroll**.<br /><br /> Lorsqu’une application définit cela dans un pilote ODBC *2.x,* cela doit indiquer un signet fixe.|  
|SQL_ATTR_ROW_STATUS_PTR|Points à la ligne de classement rempli par **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, et **SQLSetPos**.<br /><br /> Si une application le place dans un conducteur ODBC *2.x* et appelle **SQLBulkOperation** avec une *opération* de SQL_ADD avant d’appeler **SQLFetchScroll**, **SQLFetch**, ou **SQLExtendedFetch**, SQLSTATE HY011 (Attribut ne peut pas être fixé maintenant) est retourné.<br /><br /> Lorsqu’une application appelle **SQLFetch** dans un conducteur ODBC *2.x,* **SQLFetch** est cartographié sur **SQLExtendedFetch** et retourne donc des valeurs dans ce tableau.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Indique le tampon dans lequel **SQLFetch** et **SQLFetchScroll** retournent le nombre de rangées récupérées.<br /><br /> Lorsqu’une application appelle **SQLFetch** dans un conducteur ODBC *2.x,* **SQLFetch** est cartographié sur **SQLExtendedFetch** et retourne donc une valeur dans ce tampon.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Définit la taille de l’aviron.<br /><br /> Si une application appelle **SQLBulkOperations** avec une *opération* de SQL_ADD dans un conducteur ODBC *2.x,* SQL_ROWSET_SIZE sera utilisé pour l’appel, et non SQL_ATTR_ROW_ARRAY_SIZE, parce que l’appel est cartographié à **SQLSetPos** avec une *opération* de SQL_ADD, qui utilise SQL_ROWSET_SIZE.<br /><br /> Appeler **SQLSetPos** avec une *opération* de SQL_ADD ou **SQLExtendedFetch** dans un conducteur ODBC *2.x* utilise SQL_ROWSET_SIZE.<br /><br /> Appeler **SQLFetch** ou **SQLFetchScroll** dans un conducteur ODBC *2.x* utilise SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLBulkOperations (SQLBulkOperations)**|Effectue des opérations d’insertion et de signet. Lorsque **SQLBulkOperations** avec une *opération* de SQL_ADD est appelé dans un conducteur ODBC *2.x,* il est cartographié à **SQLSetPos** avec une *opération* de SQL_ADD. Voici les détails de la mise en œuvre :<br /><br /> - Lorsque vous travaillez avec un conducteur ODBC *2.x,* une application ne doit utiliser que l’ARD implicitement alloué associé à la *DéclarationHandle*; il ne peut pas allouer un autre ARD pour l’ajout de lignes, parce que les opérations explicites descripteur ne sont pas prises en charge dans un pilote ODBC *2.x.* Une application doit utiliser **SQLBindCol** pour se lier à l’ARD, pas **SQLSetDescField** ou **SQLSetDescRec**.<br />- Lorsque vous appelez un conducteur ODBC *3.x,* une application peut appeler **SQLBulkOperations** avec une *opération* de SQL_ADD avant d’appeler **SQLFetch** ou **SQLFetchScroll**. Lorsque vous appelez un conducteur ODBC *2.x,* une application doit appeler **SQLFetchScroll** avant d’appeler **SQLBulkOperations** avec une opération de SQL_ADD.|  
|**SQLFetch**|Retourne le jeu de ligne suivant. Voici les détails de la mise en œuvre :<br /><br /> - Lorsqu’une application appelle **SQLFetch** dans un conducteur ODBC *2.x,* elle est cartographiée à **SQLExtendedFetch**.<br />- Lorsqu’une application appelle **SQLFetch** dans un pilote ODBC *3.x,* elle renvoie le nombre de lignes spécifiées avec l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration.|  
|**SQLFetchScroll**|Retourne le jeu de ligne spécifié. Voici les détails de la mise en œuvre :<br /><br /> - Lorsqu’une application appelle **SQLFetchScroll** dans un pilote ODBC *2.x,* elle renvoie SQLSTATE 01S01 (Erreur de ligne) avant chaque erreur qui s’applique à une seule rangée. Il ne le fait que parce que l’ODBC *3.x* Driver Manager cartes cela à **SQLExtendedFetch** et **SQLExtendedFetch** retourne ce SQLSTATE. Lorsqu’une application appelle **SQLFetchScroll** dans un pilote ODBC *3.x,* elle ne retourne jamais SQLSTATE 01S01 (Erreur de ligne).<br />- Lorsqu’une demande appelle **SQLFetchScroll** dans un pilote ODBC *2.x* avec *FetchOrientation* réglé pour SQL_FETCH_BOOKMARK, l’argument *FetchOffset* doit être réglé à 0. SQLSTATE HYC00 (fonction facultative non mise en œuvre) est retourné si le signets compensant est tenté avec un conducteur ODBC *2.x.*|  
  
> [!NOTE]  
>  Les applications ODBC *3.x* ne doivent pas utiliser **SQLExtendedFetch** ou l’attribut de l’SQL_ROWSET_SIZE. Au lieu de cela, ils devraient utiliser **SQLFetchScroll** et l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration. Les applications ODBC *3.x* ne doivent pas utiliser **SQLSetPos** avec une *opération* de SQL_ADD, mais devraient utiliser **SQLBulkOperations** avec une *opération* de SQL_ADD.
