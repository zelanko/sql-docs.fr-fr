---
title: Curseurs de bloc, curseurs avec défilement et compatibilité descendante | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66b4cf0ce2b2ffc15a9e450461021a9b20b1f0c3
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67794134"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Curseurs de bloc, curseurs avec défilement et compatibilité descendante
L’existence des deux **SQLFetchScroll** et **SQLExtendedFetch** représente la première clear Fractionner dans ODBC entre l’Interface API (Application Programming), qui est l’ensemble de fonctions le les appels de l’application et l’Interface de fournisseur de Service (SPI), qui est l’ensemble de fonctions le pilote implémente. Cette distinction est nécessaire afin que ODBC *3.x*, qui utilise **SQLFetchScroll**, bealigned avec les normes et également être compatible avec ODBC *2.x*, qui utilise **SQLExtendedFetch**.  
  
 ODBC *3.x* API, qui est l’ensemble de l’application appelle les fonctions, inclut **SQLFetchScroll** et les attributs d’instruction. ODBC *3.x* SPI, qui est l’ensemble de fonctions, le pilote implémente, inclut **SQLFetchScroll**, **SQLExtendedFetch**et les attributs d’instruction. Comme ODBC n’applique pas formellement cette distinction entre l’API et le SPI, il est possible pour ODBC *3.x* applications d’appeler **SQLExtendedFetch** et les attributs d’instruction. Toutefois, il n’existe aucune raison pour ODBC *3.x* application pour ce faire. Pour plus d’informations sur les API et SPI, reportez-vous à l’introduction [Architecture ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Pour plus d’informations sur les fonctions et l’instruction attributs d’une application ODBC *3.x* application doit utiliser avec bloc et de curseurs avec défilement, consultez [curseurs de bloc, curseurs avec défilement et compatibilité descendante pour ODBC 3.x Applications](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Ce que fait le gestionnaire de pilotes](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Ce que fait le pilote](../../../odbc/reference/appendixes/what-the-driver-does.md)
