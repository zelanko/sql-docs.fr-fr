---
title: Utilisation de Variables et paramètres (MDX) | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 039668b719a2c6c715139682496117b8239425aa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="using-variables-and-parameters-mdx"></a>Utilisation de variables et de paramètres (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Principes de base de script MDX & #40 ; Analysis Services & #41 ;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
  
