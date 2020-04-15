---
title: Concordurrency optimiste (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- optimistic concurrency [ODBC]
ms.assetid: 9d71e09e-bc68-4c1f-9229-ed2a7be7d324
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 30eba3ea03b4c798a74a8cb928014b582846607b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282482"
---
# <a name="optimistic-concurrency"></a>Accès concurrentiel optimiste
*La concordance optimiste* tire son nom de l’hypothèse optimiste selon laquelle des collisions entre les transactions se produiront rarement; une collision se serait produite lorsqu’une autre transaction met à jour ou supprime une série de données entre le moment où elle est lue par la transaction actuelle et le moment où elle est mise à jour ou supprimée. C’est le contraire de la *concordance pessimiste,* ou le verrouillage, dans lequel le développeur d’applications croit que de telles collisions sont monnaie courante.  
  
 En accord optimiste, une rangée est laissée débloquée jusqu’à ce que le moment vienne de la mettre à jour ou de la supprimer. À ce moment-là, la rangée est relue et vérifiée pour voir si elle a été changée depuis sa dernière lecture. Si la ligne a changé, la mise à jour ou la suppression échoue et doit être essayée à nouveau.  
  
 Pour déterminer si une ligne a été modifiée, sa nouvelle version est vérifiée par rapport à une version mise en cache de la ligne. Cette vérification peut être basée sur la version de ligne, comme la colonne de timestamp dans SQL Server, ou les valeurs de chaque colonne dans la rangée. De nombreux DBMS ne prennent pas en charge les versions de ligne.  
  
 La concurrence optimiste peut être mise en œuvre par la source de données ou l’application. Dans les deux cas, l’application devrait utiliser un faible niveau d’isolement des transactions comme Read Committed; l’utilisation d’un niveau supérieur nie l’augmentation de la concurrence acquise en utilisant une concordance optimiste.  
  
 Si la source de données est mise en œuvre de la concordance optimiste, l’application définit l’attribut SQL_ATTR_CONCURRENCY énoncé à SQL_CONCUR_ROWVER ou SQL_CONCUR_VALUES. Pour mettre à jour ou supprimer une ligne, il exécute une mise à jour positionnée ou supprime une déclaration ou des appels **SQLSetPos** comme il le ferait avec une concordance pessimiste; le conducteur ou la source de données renvoie SQLSTATE 01001 (conflit d’exploitation cursor) si la mise à jour ou la suppression échoue en raison d’une collision.  
  
 Si l’application elle-même met en œuvre une concordance optimiste, elle définit l’attribut SQL_ATTR_CONCURRENCY énoncé à SQL_CONCUR_READ_ONLY de lire une ligne. S’il compare les versions de ligne et ne connaît pas la colonne de version de ligne, il appelle **SQLSpecialColumns** avec la SQL_ROWVER option pour déterminer le nom de cette colonne.  
  
 L’application met à jour ou supprime la ligne en augmentant la concordance à SQL_CONCUR_LOCK (pour obtenir l’accès à la ligne d’écriture) et l’exécution d’une **mise À JOUR** ou **d’une** déclaration DELETE avec une clause **WHERE** qui spécifie la version ou les valeurs de la ligne avait lorsque l’application la lisait. Si la ligne a changé depuis, la déclaration échouera. Si la clause **WHERE** n’identifie pas uniquement la ligne, l’instruction peut également mettre à jour ou supprimer d’autres lignes; les versions de ligne identifient toujours de façon unique les lignes, mais les valeurs de ligne n’identifient uniquement les lignes que si elles incluent la clé principale.
