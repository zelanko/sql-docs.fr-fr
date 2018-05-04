---
title: La bibliothèque de curseurs ODBC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- scrollable cursors [ODBC]
- cursors [ODBC], cursor library
- block cursors [ODBC]
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bbe54f6ba699bda96ce5a5ebb80a3d0988a41726
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="the-odbc-cursor-library"></a>La bibliothèque de curseurs ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Bloc et les curseurs de défilement sont des ajouts très utiles à de nombreuses applications. Toutefois, pas tous les pilotes prennent en charge les blocs et les curseurs de défilement. La même a la valeur true de la mise à jour positionnée et supprimer les instructions et **SQLSetPos**, qui sont présentées dans la mise à jour des données. Par conséquent, le composant ODBC du SDK Windows, précédemment inclus dans le Kit de développement logiciel, Microsoft données Access Components (MDAC) inclut une bibliothèque de curseurs. La bibliothèque de curseurs implémente les blocs, les curseurs statiques, mise à jour positionnée et les instructions delete, et **SQLSetPos** pour un pilote qui est conforme au niveau de conformité ouvrir groupe Standard CLI. La bibliothèque de curseurs peut-être être redistribuée avec les applications ODBC ; consultez le contrat de licence dans le Kit de développement logiciel pour plus d’informations.  
  
 Pour utiliser la bibliothèque de curseurs, une application définit l’attribut de connexion SQL_ATTR_ODBC_CURSORS avant de se connecter à la source de données. Pour plus d’informations sur la bibliothèque de curseurs, consultez [bibliothèque de curseurs ODBC annexe f :](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
