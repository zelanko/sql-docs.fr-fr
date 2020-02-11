---
title: Possibilité de valeur null et comparaisons logiques de trois valeurs | Microsoft Docs
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
ms.openlocfilehash: e5dbdf757038abbf2c98d3987ee14a9cb9184a61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081319"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Possibilité de valeur Null et comparaisons logiques de trois valeurs
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Si vous êtes familiarisé avec les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données, vous trouverez la sémantique et la précision similaires dans l’espace de noms **System. Data. SqlTypes** dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Il existe toutefois certaines différences, dont les principales sont décrites dans cette rubrique.  
  
## <a name="null-values"></a>Valeurs Null  
 L'une des principales différences entre les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les types de données CLR (Common Language Runtime) natifs porte sur le fait que ceux-ci n'autorisent pas les valeurs Null, tandis que ceux-là fournissent une sémantique Null complète.  
  
 Les comparaisons sont affectées par les valeurs Null. Lors de la comparaison de deux valeurs x et y, si x ou y a la valeur Null, certaines comparaisons logiques évaluent à une valeur UNKNOWN plutôt que true ou false.  
  
## <a name="sqlboolean-data-type"></a>Type de données SqlBoolean  
 L’espace de noms **System. Data. SqlTypes** introduit un type **SqlBoolean** pour représenter cette logique à 3 valeurs. Les comparaisons entre n’importe quelle **SqlTypes** retournent un type valeur **SqlBoolean** . La valeur inconnue est représentée par la valeur null du type **SqlBoolean** . Les propriétés **IsTrue**, **IsFalse**et **IsNull** sont fournies pour vérifier la valeur d’un type **SqlBoolean** .  
  
## <a name="operations-functions-and-null-values"></a>Opérations, fonctions et valeurs Null  
 Tous les opérateurs arithmétiques (+, \*-,,/,%), les opérateurs de bits (~, & et |) et la plupart des fonctions retournent Null si l’un des opérandes ou arguments de **SqlTypes** a la valeur null. La propriété **IsNull** retourne toujours une valeur true ou false.  
  
## <a name="precision"></a>Precision  
 Les types de données décimaux dans le CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ont des valeurs maximales différentes de celles des types de données numériques et décimaux dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. De plus, dans le CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], les types de données décimaux supposent la précision maximale. Dans le CLR pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], toutefois, **SqlDecimal** fournit les mêmes précision et échelle maximales, et la même sémantique que le type de données décimal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans.  
  
## <a name="overflow-detection"></a>Détection de dépassement de capacité  
 Dans le CLR [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], l'addition de deux très grands nombres peut ne pas lever d'exception. Au lieu de cela, si aucun opérateur de contrôle n'a été utilisé, le résultat retourné peut être « enveloppé » en tant qu'entier négatif. Dans **System. Data. SqlTypes**, les exceptions sont levées pour toutes les erreurs de dépassement de capacité et de dépassement de capacité négatif, et les erreurs de division par zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
