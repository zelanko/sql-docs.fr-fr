---
title: Règles d’affectation des noms d’objets (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ba1b1b3b8d8fa3f26af84ef12f95858ac32cdeee
ms.sourcegitcommit: 12b7e3447ca2154ec2782fddcf207b903f82c2c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957325"
---
# <a name="object-naming-rules-analysis-services"></a>Règles d'attribution de noms aux objets (Analysis Services)
  Cette rubrique décrit les conventions d'attribution de noms aux objets, ainsi que les caractères et les mots réservés qui ne peuvent pas être utilisés dans un nom d'objet, dans le code ou dans un script dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
##  <a name="bkmk_Names"></a>Conventions d’affectation des noms  
 Chaque objet a une propriété `Name` et `ID` qui doit être unique dans l'étendue de la collection parente. Par exemple, deux dimensions peuvent porter le même nom dans la mesure où chacune réside dans une base de données différente.  
  
 Bien que vous puissiez le spécifier manuellement, l'`ID` est en principe généré automatiquement lorsque l'objet est créé. Vous ne devez jamais modifier l'`ID` une fois que vous avez démarré la création d'un modèle. Toutes les références d'objet d'un modèle sont basées sur l'`ID`. Par conséquent, modifier un `ID` peut facilement provoquer une altération du modèle.  
  
 Pour les objets `DataSource` et `DataSourceView`, des exceptions notables aux conventions d'affectation de noms s'appliquent. L'ID `DataSource` peut être défini comme un seul point (.), non unique, comme référence à la base de données active. Une seconde exception concerne `DataSourceView`, qui adhère aux conventions d'affectation de noms définies pour les objets `DataSet` dans le .NET Framework, où `Name` est utilisé comme identifiant.  
  
 Les règles suivantes s'appliquent aux propriétés `Name` et `ID`.  
  
-   Les noms ne respectent pas la casse. Vous ne pouvez pas avoir un cube nommé «ventes» et un autre nommé «ventes» dans la même base de données.  
  
-   Aucun espace de début ou de fin n'est autorisé dans un nom d'objet, bien que vous puissiez inclure des espaces dans un nom. Les espaces de début ou de fin sont tronqués implicitement. Cela s'applique à la fois à `Name` et à l'`ID` d'un objet.  
  
-   Le nombre maximal de caractères autorisé est de 100.  
  
-   Il n'y a aucune spécification spéciale pour le premier caractère d'un identificateur. Le premier caractère peut être tout caractère valide.  
  
##  <a name="bkmk_reserved"></a>Mots et caractères réservés  
 Les mots réservés sont en anglais et s'appliquent aux noms d'objet, pas aux légendes. Si vous utilisez accidentellement un mot réservé dans un nom d'objet, une erreur de validation se produit. Pour les modèles d'exploration de données et multidimensionnels, les mots réservés décrits ci-dessous ne peuvent jamais être utilisés dans un nom d'objet.  
  
 Pour les modèles tabulaires, où la compatibilité de la base de données est définie sur 1103, les règles de validation ont été assouplies pour certains objets et ne sont pas conformes aux critères de caractères étendus et de conventions d'attribution de noms de certaines applications clientes. Les bases de données qui répondent à ces critères sont soumises à des règles de validation moins rigoureuses. Dans ce cas, un nom d'objet peut éventuellement inclure un caractère restreint et néanmoins être validé.  
  
 **Mots réservés**  
  
-   AUX  
  
-   CLOCK$  
  
-   COM1 à COM9 (COM1, COM2, COM3, et ainsi de suite)  
  
-   CON  
  
-   LPT1 à LPT9 (LPT1, LPT2, LPT3, et ainsi de suite)  
  
-   NUL  
  
-   PRN  
  
-   NULL n'est autorisé comme caractère dans aucune chaîne au sein de XML  
  
 **Caractères réservés**  
  
 Le tableau ci-dessous répertorie les caractères non valides pour les objets spécifiques.  
  
|Object|Caractères non valides|  
|------------|------------------------|  
|`Server`|Suivez les conventions d'attribution des noms de serveur Windows lorsque vous nommez un objet serveur. Pour plus d'informations, consultez [Conventions d'attribution des noms (Windows)](/windows/desktop/DNS/naming-conventions) .|  
|`DataSource`| `: / \ * \| ? " () [] {} <>` |  
|`Level` ou `Attribute`|````. , ; ' ` : / \ * & \| ? " & % $ ! + = [] {} < >````|  
|`Dimension` ou `Hierarchy`|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} <,>````|  
|Tous les autres objets|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} < >````|  
  
 **Exceptions Quand les caractères réservés sont autorisés**  
  
 Comme indiqué, les bases de données d'une modalité et d'un niveau de compatibilité spécifiques peuvent avoir des noms d'objet qui contiennent des caractères réservés. Un attribut de dimension, une hiérarchie, un niveau, une mesure et des noms d'objets d'indicateur de performance clé (KPI) peuvent comprendre des caractères réservés, pour les bases de données tabulaires (avec niveau de compatibilité supérieur ou égal à 1103) qui autorisent l'utilisation de caractères étendus :  
  
|Mode serveur et niveau de compatibilité de la base de données|Caractères réservés autorisés ?|  
|--------------------------------------------------|----------------------------------|  
|MOLAP (toutes les versions)|Non|  
|Tabulaire - 1050|Non|  
|Tabulaire - 1100|Non|  
|Tabulaire-1130 et versions ultérieures|Oui|  
  
 Les bases de données peuvent avoir un ModelType par défaut. La valeur par défaut est équivalente à celle du mode multidimensionnel et ne prend donc pas en charge l'utilisation de caractères réservés dans les noms de colonnes.  
  
## <a name="see-also"></a>Voir aussi  
 [Mots réservés MDX](/sql/mdx/mdx-reserved-words)   
 [Traductions &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/translations-analysis-services)   
 [XML for Analysis de &#40;conformité XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-compliance-xmla)  
  
  
