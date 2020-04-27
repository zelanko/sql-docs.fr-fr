---
title: Utilisation de variables et de paramètres (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eeb258266c489056994d8f78f80a6856602a174a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66073712"
---
# <a name="using-variables-and-parameters-mdx"></a>Utilisation de variables et de paramètres (MDX)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vous pouvez paramétrer une instruction MDX (Multidimensional Expressions). Une instruction paramétrable permet de créer des instructions génériques pouvant être personnalisées au moment de l'exécution.  
  
 Lors de la création d'une instruction paramétrable, vous devez identifier le nom du paramètre en l'ajoutant comme préfixe avec le signe arobase (@). Par exemple, @Year est un nom de paramètre valide  
  
 La syntaxe MDX ne prend en charge que les paramètres de valeurs littérales ou scalaires. Pour créer un paramètre faisant référence à un membre, un jeu ou un tuple, vous devez utiliser une fonction telle que [StrToMember](/sql/mdx/strtomember-mdx) ou [StrToSet](/sql/mdx/strtoset-mdx).  
  
 Dans l’exemple de XML for Analysis (XMLA) suivant, @CountryName le paramètre contient le pays pour lequel les données client sont récupérées :  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 Pour utiliser cette fonctionnalité avec OLE DB, vous devez utiliser l'interface `ICommandWithParameters`. Pour utiliser cette fonctionnalité avec ADOMD.Net, vous devez utiliser l’interface **AdomdCommand.Parameters** .  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base des scripts MDX &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)  
  
  
