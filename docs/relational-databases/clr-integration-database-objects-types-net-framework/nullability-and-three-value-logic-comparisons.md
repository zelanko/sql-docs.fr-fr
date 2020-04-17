---
title: Comparaisons de la logique de nullabilité et de trois valeurs (fr) Microsoft Docs
description: Cet article couvre la façon dont les types de données SQL Server diffèrent des types dans System.Data.SqlTypes dans le cadre .NET, qui ont la sémantique et la précision similaires.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f016abf2113afef3e02f01fd9842b91b742d50a
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488444"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Possibilité de valeur Null et comparaisons logiques de trois valeurs
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Si vous êtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] familier avec les types de données, vous trouverez la sémantique similaire et [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]la précision dans le **System.Data.SqlTypes** namespace dans le . Il existe toutefois certaines différences, dont les principales sont décrites dans cette rubrique.  
  
## <a name="null-values"></a>Valeurs Null  
 L'une des principales différences entre les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les types de données CLR (Common Language Runtime) natifs porte sur le fait que ceux-ci n'autorisent pas les valeurs Null, tandis que ceux-là fournissent une sémantique Null complète.  
  
 Les comparaisons sont affectées par les valeurs Null. Lors de la comparaison de deux valeurs x et y, si x ou y a la valeur Null, certaines comparaisons logiques évaluent à une valeur UNKNOWN plutôt que true ou false.  
  
## <a name="sqlboolean-data-type"></a>Type de données SqlBoolean  
 Le **namespace System.Data.SqlTypes** introduit un type **SqlBoolean** pour représenter cette logique à 3 valeurs. Les comparaisons entre n’importe quel **SqlTypes** renvoient un type de valeur **SqlBoolean.** La valeur UNKNOWN est représentée par la valeur nulle du type **SqlBoolean.** Les propriétés **IsTrue**, **IsFalse**, et **IsNull** sont fournis pour vérifier la valeur d’un type **SqlBoolean.**  
  
## <a name="operations-functions-and-null-values"></a>Opérations, fonctions et valeurs Null  
 Tous les opérateurs arithmétiques \*(, -, ,, /, %), les opérateurs bitwise (, &, et ),), et la plupart des fonctions retournent NULL si l’un des opérands ou des arguments de **SqlTypes** sont NULL. La propriété **IsNull** rapporte toujours une valeur vraie ou fausse.  
  
## <a name="precision"></a>Precision  
 Les types de données décimaux dans le CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ont des valeurs maximales différentes de celles des types de données numériques et décimaux dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. De plus, dans le CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], les types de données décimaux supposent la précision maximale. Dans le CLR pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cependant, **SqlDecimal** fournit la même précision maximale et l’échelle, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et la même sémantique que le type de données décimales dans .  
  
## <a name="overflow-detection"></a>Détection de dépassement de capacité  
 Dans le CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], l'addition de deux très grands nombres peut ne pas lever d'exception. Au lieu de cela, si aucun opérateur de contrôle n'a été utilisé, le résultat retourné peut être « enveloppé » en tant qu'entier négatif. Dans **System.Data.SqlTypes**, des exceptions sont prévues pour toutes les erreurs de débordement et de sous-flux, et les erreurs de division par zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
