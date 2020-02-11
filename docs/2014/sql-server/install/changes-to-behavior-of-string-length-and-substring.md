---
title: Modifications du comportement de String-Length et substring | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2119b7ba-2e52-44bf-ac57-82c2d46a48ff
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18643dfc11d2b1b1d875a19c478f9ec8cbdd5be6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66428849"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>Modifications du comportement de string-length et substring
  La [fonction de longueur de chaîne &#40;xquery&#41;](/sql/xquery/functions-on-string-values-string-length) et la [fonction de sous-chaîne &#40;fonctions XQuery&#41;](/sql/xquery/functions-on-string-values-substring) peuvent retourner des résultats différents lorsqu’elles sont utilisées avec des bases de données XML qui contiennent des caractères de substitution.  
  
## <a name="description"></a>Description  
 Lorsqu’une base de données est configurée pour [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]être compatible avec, le comportement de la [fonction de longueur de chaîne &#40;XQuery&#41;](/sql/xquery/functions-on-string-values-string-length) et la [fonction de sous-chaîne &#40;fonctions de&#41;XQuery](/sql/xquery/functions-on-string-values-substring) change lors du traitement de caractères Unicode supplémentaires. Chaque caractère Unicode supplémentaire, qui est défini en ayant un point de code supérieur à U+FFFF, est compté comme un caractère par ces fonctions au lieu de deux, comme c'était le cas dans les versions précédentes.  
  
 Pour plus d'informations sur les caractères de substitution, consultez [Surrogates and Supplementary Characters (en anglais)](https://go.microsoft.com/fwlink/?LinkId=178317).  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
