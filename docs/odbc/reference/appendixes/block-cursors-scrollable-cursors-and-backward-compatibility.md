---
title: Bloquer les curseurs, les curseurs défilementables et la compatibilité vers l’arrière ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe24362f1a49577a7fb494f768947080d0ab6e9e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292309"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>Curseurs de bloc, curseurs avec défilement et compatibilité descendante
L’existence de **SQLFetchScroll** et **SQLExtendedFetch** représente la première scission claire dans ODBC entre l’interface de programmation d’applications (API), qui est l’ensemble des fonctions des appels d’application, et l’interface fournisseur de services (SPI), qui est l’ensemble des fonctions que le conducteur met en œuvre. Cette scission est nécessaire de sorte que ODBC *3.x*, qui utilise **SQLFetchScroll**, aligné avec les normes et également être compatible avec ODBC *2.x*, qui utilise **SQLExtendedFetch**.  
  
 L’API ODBC *3.x,* qui est l’ensemble des fonctions des appels d’application, comprend **SQLFetchScroll** et les attributs de déclaration connexes. L’ODBC *3.x* SPI, qui est l’ensemble des fonctions que le conducteur met en œuvre, comprend **SQLFetchScroll**, **SQLExtendedFetch**, et les attributs de déclaration connexes. Étant donné qu’ODBC n’applique pas officiellement cette division entre l’API et le SPI, il est possible pour les applications ODBC *3.x* d’appeler **SQLExtendedFetch** et les attributs de déclaration connexes. Cependant, il n’y a aucune raison pour l’application ODBC *3.x* pour ce faire. Pour plus d’informations sur les API et les IFS, voir l’introduction à [ODBC Architecture](../../../odbc/reference/odbc-architecture.md).  
  
 Pour plus d’informations sur les fonctions et les attributs de l’instruction qu’une application ODBC *3.x* doit utiliser avec des curseurs de blocs et défilements, voir [les curseurs de bloc, les curseurs défilements et la compatibilité vers l’arrière pour les applications ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Ce que fait le gestionnaire de pilotes](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [Ce que fait le pilote](../../../odbc/reference/appendixes/what-the-driver-does.md)
