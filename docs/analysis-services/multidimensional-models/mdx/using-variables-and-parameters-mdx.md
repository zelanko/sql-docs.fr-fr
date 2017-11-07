---
title: "Utilisation de Variables et paramètres (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5ac634400b85e49cdaf9f57e683cc13fe781ed2b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="using-variables-and-parameters-mdx"></a>Utilisation de variables et de paramètres (MDX)
  Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vous pouvez paramétrer une instruction MDX (Multidimensional Expressions). Une instruction paramétrable permet de créer des instructions génériques pouvant être personnalisées au moment de l'exécution.  
  
 Lors de la création d'une instruction paramétrable, vous devez identifier le nom du paramètre en l'ajoutant comme préfixe avec le signe arobase (@). Par exemple, @Year serait un nom de paramètre valide  
  
 La syntaxe MDX ne prend en charge que les paramètres de valeurs littérales ou scalaires. Pour créer un paramètre faisant référence à un membre, un jeu ou un tuple, vous devez utiliser une fonction telle que [StrToMember](../../../mdx/strtomember-mdx.md) ou [StrToSet](../../../mdx/strtoset-mdx.md).  
  
 Dans le code XML suivant par exemple des Analysis (XMLA), le @CountryName paramètre contient le pays pour le client auquel les données sont récupérées :  
  
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
  
 Pour utiliser cette fonctionnalité avec OLE DB, vous devez utiliser l’interface **ICommandWithParameters** . Pour utiliser cette fonctionnalité avec ADOMD.Net, vous devez utiliser l’interface **AdomdCommand.Parameters** .  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base des scripts MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
  

