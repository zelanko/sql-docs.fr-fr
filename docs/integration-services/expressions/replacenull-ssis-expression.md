---
description: REPLACENULL (expression SSIS)
title: REPLACENULL (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 70db7832-b5a0-4db5-a8ad-42ad8630d8e8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f90bf0dfc2eba97d8a0c1b8b2e9bd7cdf8a0e565
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477461"
---
# <a name="replacenull-ssis-expression"></a>REPLACENULL (expression SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Retourne la valeur du paramètre de la seconde expression si la valeur du paramètre de la première expression est NULL ; sinon, retourne la valeur de la première expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
REPLACENULL(expression 1,expression 2)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression 1*  
 Le résultat de cette expression est comparé à NULL.  
  
 *expression 2*  
 Le résultat de cette expression est retourné si la première expression renvoie la valeur NULL.  
  
## <a name="result-types"></a>Types des résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes  
  
-   La longueur de l'argument *expression 2* peut être égale à zéro.  
  
-   La fonction REPLACENULL renvoie un résultat NULL si un argument est NULL.  
  
-   Les colonnes BLOB (DT_TEXT, DT_NTEXT, DT_IMAGE) ne sont pas prises en charge pour l'un ou l'autre paramètre.  
  
-   Il est prévu que les deux expressions aient le même type de retour. Dans le cas contraire, la fonction tente d'effectuer un cast de la seconde expression en type de retour de la première expression, ce qui peut se traduire par une erreur si les types de données sont incompatibles.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant remplace toute valeur NULL dans une colonne de base de données par une chaîne (1900-01-01). Cette fonction est particulièrement utilisée dans les modèles de colonne dérivée courants où vous souhaitez remplacer les valeurs NULL par autre chose.  
  
```  
REPLACENULL(MyColumn, "1900-01-01")  
```  
  
> [!NOTE]
>  Vous trouverez ci-après un exemple d’utilisation dans [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]/ [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].  
  
```  
(DT_DBTIMESTAMP) (ISNULL(MyColumn) ? "1900-01-01" : MyColumn)   
```  
  
  
