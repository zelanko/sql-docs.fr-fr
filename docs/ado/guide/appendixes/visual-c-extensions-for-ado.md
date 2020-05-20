---
title: Extensions de Visual C++ pour ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
author: rothja
ms.author: jroth
ms.openlocfilehash: f623bd3eb0c0c4cdde47c6fea7e7cd8af2ad0de6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761517"
---
# <a name="visual-c-extensions-for-ado"></a>Extensions Visual C++ pour ADO
La méthode recommandée pour programmer ADO avec Visual C++ consiste à utiliser la directive **#import** , comme indiqué dans [Microsoft Visual C++ programmation ADO](../../../ado/guide/appendixes/visual-c-ado-programming.md). Toutefois, les versions antérieures d’ADO étaient fournies avec une autre méthode de programmation à l’aide de Visual C++ : les extensions Visual C++. Cette section documente cette fonctionnalité pour ceux qui doivent gérer Visual C++ code d’extensions, mais le nouveau code ADO doit être écrit à l’aide de #**Import**.

 L’un des travaux les plus fastidieux Visual C++ les programmeurs lorsque vous récupérez des données à l’aide d’ADO consiste à convertir les données retournées en tant que type de données VARIANT en un type de données C++, puis à stocker les données converties dans une classe ou une structure. En plus d’être fastidieux, la récupération de données C++ via un type de données VARIANT diminue les performances.

 ADO fournit une interface qui prend en charge la récupération de données dans des types de données C/C++ natifs sans passer par une variante, et fournit également des macros de préprocesseur qui simplifient l’utilisation de l’interface. Le résultat est un outil flexible qui est plus facile à utiliser et qui offre de bonnes performances.

 Un scénario client C/C++ courant consiste à lier un enregistrement dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) à une classe ou un struct c/c++ contenant des types c/c++ natifs. En passant par les VARIANTs, cela implique l’écriture de code de conversion de VARIANT en types natifs C/C++. Les extensions Visual C++ pour ADO visent à rendre ce scénario beaucoup plus facile pour le programmeur Visual C++.

 Consultez les rubriques suivantes pour en savoir plus sur les extensions de Visual C++ pour ADO.

-   [Utilisation des extensions de Visual C++ pour ADO](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [En-tête d’extensions Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [Exemple ADO avec Visual C++ extensions](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>Voir aussi
 Exemple d' [index de syntaxe ADO for Visual C++ pour COM](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md) [à l’aide](../../../ado/guide/appendixes/using-visual-c-extensions.md) des extensions de Visual C++ [Visual C++ en-tête extensions](../../../ado/guide/appendixes/visual-c-extensions-header.md)
