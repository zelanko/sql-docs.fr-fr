---
description: Utilisation de procédures stockées (MDX)
title: Utilisation de procédures stockées (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2c9bd8f20ffae61656dd30f139ce12665ff57f4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476971"
---
# <a name="using-stored-procedures-mdx"></a>Utilisation de procédures stockées (MDX)


  Vous pouvez étendre les fonctionnalités de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et MDX (Multidimensional Expressions) en écrivant des fonctions définies par l'utilisateur ou des procédures stockées .NET. Pour plus d’informations, consultez [ADOMD.NET Server Programming](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
 Lorsque vous référencez ou appelez une procédure stockée, vous spécifiez le nom de la fonction, suivi de parenthèses. Dans les parenthèses, vous pouvez spécifier des expressions appelées arguments qui fournissent les données à transmettre aux paramètres. Lorsque vous appelez une fonction, vous devez fournir des valeurs d'arguments pour tous les paramètres, en respectant l'ordre dans lequel les paramètres sont définis dans la fonction définie par l'utilisateur.  
  
 L'exemple de requête suivant suppose que vous avez un assembly nommé SampleAssembly inscrit sur votre serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] :  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  La *procédure stockée* est la terminologie utilisée dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour ces types de fonctions. Les versions antérieures de ont [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] appelé ces types de fonctions en tant que *fonctions définies par l’utilisateur*.  
  
## <a name="types-of-stored-procedures"></a>Types de procédures stockées  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge à la fois les assemblys COM et CLR. Les assemblys CLR sont recommandés en raison de la sécurité renforcée dont ils disposent. Si Microsoft Office Excel est installé sur le serveur, les fonctions Excel sont également disponibles.  
  
> [!NOTE]  
>  Les assemblys COM de Microsoft Visual Basic pour Applications (VBA) sont enregistrés automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;syntaxe MDX&#41;](../mdx/functions-mdx-syntax.md)  
  
  
