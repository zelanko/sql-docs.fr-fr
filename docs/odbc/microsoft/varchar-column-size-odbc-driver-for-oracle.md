---
title: Taille des colonnes VARCHAR (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db2871324f92ef6d84a8bf8313db105489100a96
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63232161"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>Taille des colonnes VARCHAR (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Dans Oracle8, la taille maximale d’une colonne VARCHAR a augmenté de 2000 à 4 000 octets. Le logiciel client de 7.3.x Oracle n’a aucun moyen pour lier une valeur de paramètre supérieure à 2 000 octets. Par conséquent, si vous créez une table avec une colonne VARCHAR de plus de 2 000 octets, vous ne pourrez pas effectuer des insertions paramétrables, les mises à jour, les suppressions et les requêtes avec des données qui dépassent la limite de 2000-octet du logiciel client. Étant donné qu’à la fois le pilote ODBC pour Oracle et le fournisseur OLE DB pour Oracle utilisent des requêtes, les mises à jour, suppressions et insertions paramétrées, ils signale les ORA-01026 erreurs dans ce cas. Les données qui se trouve dans les limites appliquées par le logiciel client Oracle fonctionnera. Pour éviter cette limite en octets de 2000, vous devez mettre à niveau votre logiciel client Oracle8 (8.0.4.1.1c ou une version ultérieure).
