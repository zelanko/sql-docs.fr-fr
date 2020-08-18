---
description: Taille des colonnes VARCHAR (pilote ODBC pour Oracle)
title: Taille de colonne VARCHAR (pilote ODBC pour Oracle) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c490487f0edb15fe7d7165b79c4c5f1730a0dd22
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449061"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>Taille des colonnes VARCHAR (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Dans Oracle8, la taille maximale d’une colonne VARCHAR est passée de 2000 à 4000 octets. Le logiciel client Oracle 7.3. x n’a aucun moyen de lier une valeur de paramètre supérieure à 2000 octets. Par conséquent, si vous créez une table avec une colonne VARCHAR de plus de 2000 octets, vous ne pourrez pas effectuer des insertions, des mises à jour, des suppressions et des requêtes paramétrables avec des données qui dépassent la limite de 2000 octets du logiciel client. Étant donné que le pilote ODBC pour Oracle et le fournisseur de OLE DB pour Oracle utilisent des insertions, des mises à jour, des suppressions et des requêtes paramétrables, ils signalent les erreurs ORA-01026 dans ce cas. Les données qui se trouvent dans les limites imposées par le logiciel client Oracle fonctionnent. Pour éviter cette limite de 2000 octets, vous devez mettre à niveau votre logiciel client vers Oracle8 (8.0.4.1.1 c ou version ultérieure).
