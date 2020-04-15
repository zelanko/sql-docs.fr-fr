---
title: La Bibliothèque des cursoirs de l’ODBC (fr) Microsoft Docs
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
- scrollable cursors [ODBC]
- cursors [ODBC], cursor library
- block cursors [ODBC]
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b243e8ae2dc931830a249d4392da308e68722cdf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300049"
---
# <a name="the-odbc-cursor-library"></a>Bibliothèque de curseurs ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Les curseurs de bloc et de défilement sont des ajouts très utiles à beaucoup d’applications. Cependant, tous les conducteurs ne prennent pas en charge les curseurs de bloc et de défilement. Il en va de même pour les relevés de mise à jour et de suppression positionnés et **SQLSetPos**, qui sont discutés dans la mise à jour des données. Par conséquent, le composant ODBC du Windows SDK, anciennement inclus dans le SDK Microsoft Data Access Components (MDAC), comprend une bibliothèque de curseurs. La bibliothèque de curseurs implémente le bloc, les curseurs statiques, les instructions de mise à jour et de suppression positionnées, et **SQLSetPos** pour tout pilote qui répond au niveau de conformité CLI standard de groupe ouvert. La bibliothèque de curseurs peut être redistribuée avec des applications ODBC; voir l’accord de licence dans le SDK pour plus d’informations.  
  
 Pour utiliser la bibliothèque de curseurs, une application définit l’attribut de connexion SQL_ATTR_ODBC_CURSORS avant qu’il ne se connecte à la source de données. Pour plus d’informations sur la bibliothèque de curseurs, voir [Annexe F: ODBC Cursor Library](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
