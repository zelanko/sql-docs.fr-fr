---
title: Gestion des erreurs et avertissements (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- inline errors [XMLA]
- SOAP faults [XML for Analysis]
- XML for Analysis, errors
- faults [XML for Analysis]
- messages [XML for Analysis]
- XMLA, errors
- warnings [XML for Analysis]
- inline warnings [XMLA]
ms.assetid: ab895282-098d-468e-9460-032598961f45
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 856886a5edfa5dcae604b44f5c2dca356ba0addb
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60156386"
---
# <a name="handling-errors-and-warnings-xmla"></a>Gestion des erreurs et des avertissements (XMLA)
  Gestion des erreurs est requises lorsqu’un document XML for Analysis (XMLA) [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) ou [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) appel de méthode n’est pas exécuté, s’exécute correctement mais génère des erreurs ou avertissements, ou s’exécute correctement mais retourne des résultats qui contient des erreurs.  
  
|Error|Signalement|  
|-----------|---------------|  
|L'appel de méthode XMLA ne s'exécute pas|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Retourne un message d’erreur SOAP qui contient les détails de l’échec.<br /><br /> Pour plus d’informations, consultez la section [gestion des erreurs SOAP](#handling_soap_faults).|  
|Erreurs ou avertissements sur un appel de méthode ayant abouti|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] inclut un [erreur](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) ou [avertissement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) élément pour chaque erreur ou avertissement, respectivement, dans le [Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) propriété de la [racine](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) élément qui contient les résultats de l’appel de méthode.<br /><br /> Pour plus d’informations, consultez la section [gestion des erreurs et avertissements](#handling_errors_and_warnings).|  
|Erreurs dans les résultats d'un appel de méthode ayant abouti|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] inclut un inline `error` ou `warning` élément pour l’erreur ou l’avertissement, respectivement, dans le texte approprié [cellule](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) ou [ligne](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) élément des résultats de l’appel de méthode.<br /><br /> Pour plus d’informations, consultez la section [gestion des erreurs d’Inline et les avertissements](#handling_inline_errors_and_warnings).|  
  
##  <a name="handling_soap_faults"></a> Gestion des erreurs SOAP  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne une erreur SOAP lorsque les situations suivantes se présentent :  
  
-   le message SOAP qui contient la méthode XMLA n'était pas correctement formé ou n'a pas pu être validé par l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ;  
  
-   une communication ou une autre erreur s'est produite impliquant le message SOAP qui contient la méthode XMLA ;  
  
-   la méthode XMLA ne s'est pas exécutée sur l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Les codes d'erreur SOAP pour XMLstartA commencent par « XMLForAnalysis », suivis d'un point et du code de résultat hexadécimal HRESULT. Par exemple, le code d'erreur « `0x80000005` » prend la forme « `XMLForAnalysis.0x80000005` ». Pour plus d'informations sur le format d'erreur SOAP, consultez la rubrique consacrée aux erreurs Soap dans le document « Simple Object Access Protocol (SOAP) 1.1 » du W3C (en anglais).  
  
### <a name="fault-code-information"></a>Informations de code d'erreur  
 Le tableau suivant présente les informations de code d'erreur XMLA contenues dans la section détaillée de la réponse SOAP. Les colonnes représentent les attributs d'une erreur dans la section détaillée d'une erreur SOAP.  
  
|Nom de colonne|Type|Description|Null autorisé<sup>1</sup>|  
|-----------------|----------|-----------------|------------------------------|  
|`ErrorCode`|`UnsignedInt`|Code de retour qui indique le succès ou l'échec de la méthode. La valeur hexadécimale doit être convertie en valeur `UnsignedInt`.|Non|  
|`WarningCode`|`UnsignedInt`|Code de retour qui indique une condition d'avertissement. La valeur hexadécimale doit être convertie en valeur `UnsignedInt`.|Oui|  
|`Description`|`String`|Texte et description de l'erreur ou de l'avertissement retourné par le composant qui a généré l'erreur.|Oui|  
|`Source`|`String`|Nom du composant qui a généré l'erreur ou l'avertissement.|Oui|  
|`HelpFile`|`String`|Chemin d'accès ou URL menant au fichier ou à la rubrique d'aide qui décrit l'erreur ou l'avertissement.|Oui|  
  
 <sup>1</sup> indique si les données est obligatoire et doivent être retournées, ou si les données sont facultatives et une chaîne null est autorisée si la colonne ne s’applique pas.  
  
 Voici un exemple d'erreur SOAP qui s'est produite à l'occasion d'un échec d'appel de méthode :  
  
```  
<?xml version="1.0"?>  
   <SOAP-ENV:Envelope  
   xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
   SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
      <SOAP-ENV:Fault>  
         <faultcode>XMLAnalysisError.0x80000005</faultcode>  
         <faultstring>The XML for Analysis provider encountered an error.</faultstring>  
         <faultactor>XML for Analysis Provider</faultactor>  
         <detail>  
<Error  
ErrorCode="2147483653"  
Description="An unexpected error has occurred."  
Source="XML for Analysis Provider"  
HelpFile="" />  
         </detail>  
      </SOAP-ENV:Fault>  
</SOAP-ENV:Envelope>  
```  
  
##  <a name="handling_errors_and_warnings"></a> Gestion des erreurs et avertissements  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne la propriété `Messages` dans l'élément `root` d'une commande si les situations suivantes se présentent à la suite de l'exécution de cette commande :  
  
-   la méthode proprement dite n'a pas échoué, mais un échec s'est produit dans l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] après que l'appel de méthode a abouti ;  
  
-   l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne un avertissement lorsque la commande aboutit.  
  
 La propriété `Messages` suit toutes les autres propriétés contenues dans l'élément `root` et peut contenir un ou plusieurs éléments `Message`. De leur côté, les éléments `Message` peut chacun contenir un élément `error` ou `warning` décrivant, respectivement, les erreurs ou les avertissements qui se sont produits pour la commande spécifiée.  
  
 Pour plus d’informations sur les erreurs et avertissements qui sont contenus dans le `Messages` propriété, consultez [élément Messages &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla).  
  
### <a name="handling-errors-during-serialization"></a>Gestion des erreurs pendant la sérialisation  
 Si une erreur se produit après la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance a déjà commencé à sérialiser la sortie d’une commande exécutée avec succès, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne un [Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) élément dans un espace de noms différent au moment de l’erreur. L'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ferme alors tous les éléments ouverts de telle sorte que le document XML envoyé au client soit un document valide. L'instance retourne également un élément `Messages` qui contient la description de l'erreur.  
  
##  <a name="handling_inline_errors_and_warnings"></a> Gestion des erreurs insérées et avertissements  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne un élément inséré `error` ou `warning` pour une commande si la méthode XMLA proprement dite n'a pas échoué, mais qu'une erreur spécifique à un élément de données contenu dans les résultats retournés par la méthode s'est produite dans l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] après que l'appel de méthode XMLA a abouti.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit inline `error` et `warning` éléments si les problèmes spécifiques à une cellule ou à d’autres données qui sont contenus dans un `root` à l’aide de l’élément le [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) type de données se produisent, par exemple une sécurité erreur ou la mise en forme Erreur d’une cellule. Dans ces cas, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne un élément `error` ou `warning` dans l'élément `Cell` ou `row` qui contient, respectivement, l'erreur ou l'avertissement.  
  
 L’exemple suivant illustre un jeu de résultats qui contient une erreur dans l’ensemble de lignes retournée à partir d’un `Execute` à l’aide de la méthode la [instruction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) commande.  
  
```  
<return>  
   ...  
   <root>  
      ...  
      <CellData>  
      ...  
         <Cell CellOrdinal="10">  
            <Value>  
               <Error>  
                  <ErrorCode>2148497527</ErrorCode>   
                  <Description>Security Error.</Description>   
               </Error>  
            </Value>  
         </Cell>  
      </CellData>  
      ...  
   </root>  
   ...  
</return>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
