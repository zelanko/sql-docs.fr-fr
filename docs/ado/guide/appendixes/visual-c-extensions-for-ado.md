---
title: Extensions Visual C++ pour ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca21e976783a10a738488762e382982e4fd8fd8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747677"
---
# <a name="visual-c-extensions"></a>Extensions Visual C++
À l’aide de la méthode préférée de programmation ADO avec Visual C++ est la **#import** directive, comme indiqué dans [programmation ADO Visual C++](../../../ado/guide/appendixes/visual-c-ado-programming.md). Toutefois, les versions antérieures de ADO inclus dans une autre méthode de programmation à l’aide de Visual C++ : les Extensions Visual C++. Cette section décrit cette fonctionnalité pour les utilisateurs qui doivent conserver des Extensions Visual C++, mais le nouveau code ADO doit être écrits à l’aide de #**importer**.

 Une des plus fastidieux travaux Visual C++ les programmeurs sont confrontés lors de la récupération des données avec ADO consiste à convertir les données retournées comme un type de données VARIANT en un type de données C++ et puis stocker les données converties dans une classe ou structure. De plus, récupération de données C++ via un type de données VARIANT diminue les performances.

 ADO fournit une interface qui prend en charge la récupération des données en types de données C/C++ natifs sans passer par une variante et fournit également des macros de préprocesseur qui simplifient l’utilisation de l’interface. Le résultat est un outil flexible qui est plus facile à utiliser et a de bonnes performances.

 Un scénario de client C/C++ classique consiste à lier un enregistrement dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) à une structure de C/C++ ou d’une classe contenant des types C/C++ natifs. Pendant que vous parcourez les variantes, cela implique l’écriture de code de conversion de type VARIANT en types C/C++ natifs. Les Extensions Visual C++ pour ADO sont visent à rendre ce scénario beaucoup plus facile pour le programmeur Visual C++.

 Consultez les rubriques suivantes pour en savoir plus sur les Extensions Visual C++ pour ADO.

-   [À l’aide des Extensions Visual C++ pour ADO](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [En-tête d’extensions Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [ADO avec exemple d’Extensions Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>Voir aussi
 [Index de la syntaxe Visual C++ pour COM ADO pour](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [exemple d’Extensions Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md) [à l’aide des Extensions Visual C++](../../../ado/guide/appendixes/using-visual-c-extensions.md) [en-tête d’Extensions Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)
