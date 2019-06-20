---
title: Modifications apportées au comportement de string-length et substring | Microsoft Docs
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66428849"
---
# <a name="changes-to-behavior-of-string-length-and-substring"></a>Modifications du comportement de string-length et substring
  Le [fonction string-length &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) et [substring (fonction) &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) fonctions peuvent renvoyer des résultats différents lorsqu’il est utilisé avec les bases de données XML contenant caractères de substitution.  
  
## <a name="description"></a>Description  
 Quand une base de données est définie pour être compatible avec [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le comportement de la [fonction string-length &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-string-length) et [substring (fonction) &#40;XQuery&#41; ](/sql/xquery/functions-on-string-values-substring) fonctions change lors du traitement de caractères Unicode supplémentaires. Chaque caractère Unicode supplémentaire, qui est défini en ayant un point de code supérieur à U+FFFF, est compté comme un caractère par ces fonctions au lieu de deux, comme c'était le cas dans les versions précédentes.  
  
 Pour plus d'informations sur les caractères de substitution, consultez [Surrogates and Supplementary Characters (en anglais)](https://go.microsoft.com/fwlink/?LinkId=178317).  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
