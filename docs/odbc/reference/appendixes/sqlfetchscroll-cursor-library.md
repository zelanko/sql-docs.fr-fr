---
title: SQLFetchScroll (Cursor Library) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetchScroll function [ODBC], Cursor Library
ms.assetid: 4417e57c-31dd-475e-8fe9-eab00a459c80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e5573b8afc49afec8b7afa4fc52590e7a6a9e2fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302050"
---
# <a name="sqlfetchscroll-cursor-library"></a>SQLFetchScroll (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLFetchScroll** dans la bibliothèque de curseurs. Pour plus d’informations sur **SQLFetchScroll**, voir [SQLFetchScroll Function](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 La bibliothèque de curseurs met en œuvre **SQLFetchScroll** en appelant à plusieurs reprises **SQLFetch** dans le conducteur. Il transfère les données qu’il récupère du conducteur aux tampons rowset fournis par l’application. Il cache également les données dans les fichiers mémoire et disque. Lorsqu’une demande demande un nouvel acrètement, la bibliothèque de curseurs la récupère au besoin auprès du conducteur (si elle n’a pas été récupérée auparavant) ou du cache (si elle a déjà été récupérée). Enfin, la bibliothèque de curseurs conserve l’état des données mises en cache et renvoie ces informations à l’application dans le tableau d’état de la ligne.  
  
 Lorsque la bibliothèque de curseurs est utilisée, les appels à **SQLFetchScroll** ne peuvent pas être mélangés avec des appels à **SQLFetch** ou **SQLExtendedFetch**.  
  
 Lorsque la bibliothèque de curseurs est utilisée, les appels à **SQLFetchScroll** sont pris en charge à la fois pour ODBC 2. *x* et pour ODBC 3. *x* conducteurs.  
  
## <a name="rowset-buffers"></a>Tampons Rowset  
 La bibliothèque de curseurs optimise le transfert de données du conducteur vers le tampon rowset fourni par l’application si :  
  
-   L’application utilise la liaison en ligne.  
  
-   Il n’y a pas d’octets inutilisés entre les champs dans la structure que l’application déclare détenir une rangée de données.  
  
-   Les champs dans lesquels **SQLFetch** ou **SQLFetchScroll** retournent la longueur/indicateur d’une colonne suivent le tampon pour cette colonne et précèdent le tampon pour la colonne suivante. Ces champs sont facultatifs.  
  
 Lorsque l’application demande un nouveau ramset, la bibliothèque de curseurs récupère les données de son cache et du conducteur au besoin. Si les rames neuves et anciennes se chevauchent, la bibliothèque de curseurs peut optimiser ses performances en réutilisant les données des sections qui se chevauchent des tampons en rangée. Par conséquent, des modifications non apportées aux tampons encastrés sont perdues à moins que les rames nouvelles et anciennes ne se chevauchent et que les changements se trouvent dans les sections qui se chevauchent des tampons en rangée. Pour enregistrer les modifications, une demande soumet une mise à jour positionnée.  
  
 Notez que la bibliothèque de curseurs rafraîchit toujours les tampons encastré avec les données du cache lorsqu’une application appelle **SQLFetchScroll** avec *l’argument FetchOrientation* réglé pour SQL_FETCH_RELATIVE et *l’argument FetchOffset* réglé à 0.  
  
 La bibliothèque de curseurs prend en charge l’appel **SQLSetStmtAttr** avec un *attribut* de SQL_ATTR_ROW_ARRAY_SIZE pour changer la taille de l’aviron pendant qu’un curseur est ouvert. La nouvelle taille de ramset entrera en vigueur la prochaine fois **que SQLFetchScroll** est appelé.  
  
## <a name="result-set-membership"></a>Adhésion à l’ensemble des résultats  
 La bibliothèque de curseurs ne récupère les données du conducteur que lorsque l’application les demande. Selon la source de données et le paramètre de l’attribut de l’SQL_CONCURRENCY énoncé, cela a les conséquences suivantes :  
  
-   Les données récupérées par la bibliothèque de curseurs peuvent différer des données disponibles au moment de l’exécution de la déclaration. Par exemple, après l’ouverture du curseur, les rangées insérées à un point au-delà de la position de curseur actuel peuvent être récupérées par certains conducteurs.  
  
-   Les données de l’ensemble de résultats peuvent être verrouillées par la source de données pour la bibliothèque de curseurs et ne pas être disponibles pour les autres utilisateurs.  
  
 Une fois que la bibliothèque de curseurs a mis en cache une série de données, elle ne peut pas détecter les changements apportés à cette ligne dans la source de données sous-jacente (à l’exception des mises à jour positionnées et supprime l’exploitation sur le cache du même curseur). Cela se produit parce que, pour les appels à **SQLFetchScroll**, la bibliothèque de curseurs ne refetches jamais les données de la source de données. Au lieu de cela, il refaçons les données de son cache.  
  
## <a name="scrolling"></a>Défilement  
 La bibliothèque de curseurs prend en charge les types d’aller chercher suivants dans **SQLFetchScroll**.  
  
|Type de curseur|Types d’aller chercher|  
|-----------------|-----------------|  
|Curseur avant uniquement|SQL_FETCH_NEXT|  
|statique|SQL_FETCH_NEXT<br /><br /> SQL_FETCH_PRIOR<br /><br /> SQL_FETCH_FIRST<br /><br /> SQL_FETCH_LAST<br /><br /> SQL_FETCH_RELATIVE<br /><br /> SQL_FETCH_ABSOLUTE<br /><br /> SQL_FETCH_BOOKMARK|  
  
## <a name="errors"></a>Erreurs  
 Lorsque **SQLFetchScroll** est appelé et que l’un des appels à **SQLFetch** retourne SQL_ERROR, la bibliothèque de curseurs procède comme suit. Une fois qu’elle a terminé ces étapes, la bibliothèque de curseurs continue le traitement.  
  
1.  Appelle **SQLGetDiagRec** pour obtenir des informations d’erreur du conducteur et affiche cela comme un dossier de diagnostic dans le gestionnaire de conducteur.  
  
2.  Définit le champ SQL_DIAG_ROW_NUMBER dans le dossier diagnostique à la valeur appropriée.  
  
3.  Définit le champ SQL_DIAG_COLUMN_NUMBER dans le dossier diagnostique à la valeur appropriée, le cas échéant; sinon, il le définit à 0.  
  
4.  Définit la valeur de la ligne dans l’erreur dans le tableau d’état de la ligne à SQL_ROW_ERROR.  
  
 Après que la bibliothèque de curseur a appelé **SQLFetch** plusieurs fois dans sa mise en œuvre de **SQLFetchScroll**, toute erreur ou avertissement retourné par l’un des appels à **SQLFetch** sera dans un dossier de diagnostic et peut être récupéré par un appel à **SQLGetDiagRec**. Si les données ont été tronquées lorsqu’elles ont été récupérées, les données tronquées résideront désormais dans le cache de la bibliothèque de curseurs. Les appels ultérieurs à **SQLFetchScroll** pour faire défiler à une rangée avec des données tronquées retourneront les données tronquées, et aucun avertissement ne sera levé parce que les données sont récupérées à partir du cache de la bibliothèque de curseur. Pour suivre la longueur des données retournées afin qu’elles puissent déterminer si les données retournées dans un tampon ont été tronquées, une application doit lier le tampon longueur/indicateur.  
  
## <a name="bookmark-operations"></a>Opérations de signet  
 La bibliothèque de curseurs prend en charge **l’appel SQLFetchScroll** avec une *fetchOrientation* de SQL_FETCH_BOOKMARK. Il prend également en charge la spécibilité d’une compensation dans l’argument *FetchOffset* qui peut être utilisé dans l’opération de signets. C’est la seule opération de signets que la bibliothèque de curseurs prend en charge. La bibliothèque de curseurs n’appuie pas l’appel **SQLBulkOperations**.  
  
 Si l’application a défini l’attribut de l’SQL_ATTR_USE_BOOKMARKS et a lié à la colonne de signets, la bibliothèque de curseur génère un signet à durée fixe et le renvoie à l’application. La bibliothèque de curseurs crée et maintient les signets qu’elle utilise; il n’utilise pas de signets conservés à la source de données. Lorsque **SQLFetchScroll** est appelé pour récupérer un bloc de données qui a déjà été récupéré à partir de la source de données, il récupère les données du cache de la bibliothèque de curseur. Par conséquent, le signet utilisé dans un appel à **SQLFetchScroll** avec une *fetchOrientation* de SQL_FETCH_BOOKMARK doit être créé et entretenu par la bibliothèque de curseurs.  
  
## <a name="interaction-with-other-functions"></a>Interaction avec d’autres fonctions  
 Une application doit appeler **SQLFetch** ou **SQLFetchScroll** avant de préparer ou d’exécuter toute mise à jour ou suppression de relevés.
