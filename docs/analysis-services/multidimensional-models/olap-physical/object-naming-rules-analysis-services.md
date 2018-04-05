---
title: Règles d’affectation de noms (Analysis Services) de l’objet | Documents Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9b489ecceb4d8aeb5716708ae680999a296b5d14
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="object-naming-rules-analysis-services"></a>Règles d'attribution de noms aux objets (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Cette rubrique décrit les conventions d’affectation de noms d’objet, ainsi que les mots réservés et des caractères qui ne peut pas être utilisés dans un nom d’objet, dans le code ou de script dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
##  <a name="bkmk_Names"></a>Conventions d’affectation de noms  
 Chaque objet possède une propriété **Name** et une propriété **ID** qui doivent être uniques dans l'étendue de la collection parente. Par exemple, deux dimensions peuvent porter le même nom dans la mesure où chacune réside dans une base de données différente.  
  
 Bien que vous puissiez le spécifier manuellement, l' **ID** est en principe généré automatiquement lorsque l'objet est créé. Vous ne devez jamais modifier l' **ID** une fois que vous avez démarré la création d'un modèle. Toutes les références d'objet d'un modèle sont basées sur l' **ID**. Par conséquent, modifier un **ID** peut facilement provoquer une altération du modèle.  
  
 Les objets**DataSource** et **DataSourceView** présentent des exceptions notables en matière de conventions d'attribution de noms. L'ID**DataSource** peut être défini sur un point (.), qui n'est pas unique, comme référence à la base de données active. Une autre exception est **DataSourceView**, qui se conforme aux conventions d'attribution de noms définies pour les objets **DataSet** dans le .NET Framework, où **Name** est utilisé comme identificateur.  
  
 Les règles suivantes s'appliquent aux propriétés **Name** et **ID** .  
  
-   Les noms ne respectent pas la casse. Vous ne pouvez pas avoir un cube nommé « ventes » et un autre nommé « Ventes » dans la même base de données.  
  
-   Aucun espace de début ou de fin n'est autorisé dans un nom d'objet, bien que vous puissiez inclure des espaces dans un nom. Les espaces de début ou de fin sont tronqués implicitement. Cela s'applique à la fois à **Name** et à l' **ID** d'un objet.  
  
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
  
|Objet|Caractères non valides|  
|------------|------------------------|  
|**Server**|Suivez les conventions d'attribution des noms de serveur Windows lorsque vous nommez un objet serveur. Pour plus d'informations, consultez [Conventions d'attribution des noms (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682856\(v=vs.85\).aspx) .|  
|**DataSource**|: / \ * &#124; ? " () [] {} <>|  
|**Level** ou **Attribute**|. , ; ' ` : / \ * &#124; ? " & % $ ! + = [] {} < >|  
|**Dimension** ou **Hierarchy**|. , ; ' ` : / \ * &#124; ? " & % $ ! + = () [] {} \<,>|  
|Tous les autres objets|. , ; ' ` : / \ * &#124; ? " & % $ ! + = () [] {} < >|  
  
 **Exceptions : Lorsque les caractères réservés sont autorisés**  
  
 Comme indiqué, les bases de données d'une modalité et d'un niveau de compatibilité spécifiques peuvent avoir des noms d'objet qui contiennent des caractères réservés. Un attribut de dimension, une hiérarchie, un niveau, une mesure et des noms d'objets d'indicateur de performance clé (KPI) peuvent comprendre des caractères réservés, pour les bases de données tabulaires (avec niveau de compatibilité supérieur ou égal à 1103) qui autorisent l'utilisation de caractères étendus :  
  
|Mode serveur et niveau de compatibilité de la base de données|Caractères réservés autorisés ?|  
|--------------------------------------------------|----------------------------------|  
|MOLAP (toutes les versions)|non|  
|Tabulaire - 1050|non|  
|Tabulaire - 1100|non|  
|Tabulaire – 1130 et ultérieur|Oui|  
  
 Les bases de données peuvent avoir un ModelType par défaut. La valeur par défaut est équivalente à celle du mode multidimensionnel et ne prend donc pas en charge l'utilisation de caractères réservés dans les noms de colonnes.  
  
## <a name="see-also"></a>Voir aussi  
 [Mots réservés MDX](../../../mdx/mdx-reserved-words.md)   
 [Prise en charge de la traduction dans Analysis Services](../../../analysis-services/translation-support-in-analysis-services.md)   
 [XML for Analysis conformité &#40; XMLA &#41;](../../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)  
  
  
