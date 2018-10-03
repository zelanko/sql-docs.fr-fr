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
ms.openlocfilehash: d3896473a1fa08f769f13d94bd1d81f373cf67c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854503"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Curseurs de bloc, curseurs avec défilement et compatibilité descendante
L’existence des deux **SQLFetchScroll** et **SQLExtendedFetch** représente la première clear Fractionner dans ODBC entre l’Interface API (Application Programming), qui est l’ensemble de fonctions le les appels de l’application et l’Interface de fournisseur de Service (SPI), qui est l’ensemble de fonctions le pilote implémente. Cette distinction est nécessaire afin que ODBC 3. *x*, qui utilise **SQLFetchScroll**, bealigned avec les normes et également être compatible avec ODBC 2. *x*, qui utilise **SQLExtendedFetch**.  
  
 Le 3 ODBC *.x* API, qui est l’ensemble de l’application appelle les fonctions, inclut **SQLFetchScroll** et les attributs d’instruction. Le 3 ODBC *.x* SPI, qui est l’ensemble de fonctions, le pilote implémente, inclut **SQLFetchScroll**, **SQLExtendedFetch**et les attributs d’instruction. Comme ODBC n’applique pas formellement cette distinction entre l’API et le SPI, il est possible pour ODBC 3 *.x* applications d’appeler **SQLExtendedFetch** et les attributs d’instruction. Toutefois, il n’existe aucune raison pour ODBC 3 *.x* application pour ce faire. Pour plus d’informations sur les API et SPI, reportez-vous à l’introduction [Architecture ODBC](../../../odbc/reference/odbc-architecture.md).  
  
 Pour plus d’informations sur les fonctions et l’instruction d’attributs une ODBC 3. *x* application doit utiliser avec bloc et de curseurs avec défilement, consultez [curseurs de bloc, curseurs avec défilement et compatibilité descendante pour les Applications ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Ce que fait le gestionnaire de pilotes](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Ce que fait le pilote](../../../odbc/reference/appendixes/what-the-driver-does.md)
