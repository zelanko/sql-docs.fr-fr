---
title: Recherche de terme, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.termlookuptrans.f1
helpviewer_keywords:
- extracting data [Integration Services]
- match extracted terms [Integration Services]
- text extraction [Integration Services]
- term extractions [Integration Services]
- lookups [Integration Services]
- counting extracted items
- Term Lookup transformation
ms.assetid: 3c0fa2f8-cb6a-4371-b184-7447be001de1
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 546acdba2996b4264e946b052af18cf6574868a3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043180"
---
# <a name="term-lookup-transformation"></a>transformation de recherche de terme
  La transformation de recherche de terme met en correspondance des termes extraits de texte d'une colonne d'entrée de transformation avec les termes d'une table de référence. Elle compte ensuite le nombre de fois où un terme de la table de recherche apparaît dans le dataset d'entrée, puis écrit ce nombre et le terme de la table de référence dans les colonnes de la sortie de la transformation. Cette transformation est utile pour créer une liste personnalisée de termes reposant sur le texte d'entrée et complétée de statistiques de fréquence.  
  
 Avant d'effectuer une recherche, la transformation de recherche de terme extrait des mots du texte dans une colonne d'entrée à l'aide de la même méthode que la transformation d'extraction de terme :  
  
-   Le texte est divisé en phrases.  
  
-   Les phrases sont divisées en mots.  
  
-   Les mots sont normalisés.  
  
 Il est possible de configurer la transformation de recherche de terme de manière à effectuer une mise en correspondance respectant la casse.  
  
## <a name="matches"></a>Correspondances  
 La recherche de terme effectue une recherche et renvoie une valeur en suivant les règles ci-dessous :  
  
-   Si la transformation est configurée pour effectuer des mises en correspondance respectant la casse, les termes ne correspondant pas à la casse sont ignorés. Par exemple, *étudiant* et *ÉTUDIANT* sont considérés comme des termes distincts.  
  
    > [!NOTE]  
    >  Un mot dont la première lettre est une minuscule peut être mis en correspondance avec un mot dont la première lettre est une majuscule en début de phrase. Par exemple, *étudiant* et *Étudiant* sont mis en correspondance si *Étudiant* est le premier mot de la phrase.  
  
-   Si une forme plurielle du nom ou de la phrase nominale existe dans la table de référence, la recherche met en correspondance uniquement la forme plurielle du nom ou de la phrase nominale. Par exemple, les instances de *étudiants* et de *étudiant*sont comptabilisées de façon distincte.  
  
-   Si seule la forme singulier du mot se trouve dans la table de référence, les formes singulier et pluriel du mot ou de la phrase sont mises en correspondance avec la forme singulier. Par exemple, si la table de recherche contient *étudiant*et que la transformation trouve les mots *étudiant* et *étudiants*, ces deux mots seront comptabilisées comme des correspondances du terme *étudiant*.  
  
-   Si le texte de la colonne d'entrée est une phrase nominale contenant des lemmes, seul le dernier mot de la phrase nominale est affecté par la normalisation. Par exemple, la version avec lemmes de *visites avec les médecins* est *visite avec les médecins*.  
  
 Lorsqu'un élément de recherche contient des termes débordant du cadre de référence, autrement dit si un sous-terme est trouvé dans plusieurs enregistrements de référence, la transformation de recherche de terme ne renvoie qu'un seul résultat de recherche. L'exemple suivant illustre le résultat trouvé lorsqu'un élément de recherche présente un sous-terme de chevauchement. Dans cet exemple, le sous-terme est *Windows*, que l’on retrouve dans deux termes de référence. Toutefois, la transformation ne retourne pas deux résultats, mais un seul terme de référence uniquement, *Windows*. Le second terme de référence, *Windows 7 Professionnel*, n’est pas retourné.  
  
|Élément|Valeur|  
|----------|-----------|  
|Terme entré|Windows 7 Professionnel|  
|Termes de référence|Windows, Windows 7 Professionnel|  
|Sortie|Windows|  
  
 La transformation de recherche de terme peut mettre en correspondance des noms et des phrases nominales contenant des caractères spéciaux. Les données de la table de référence peuvent inclure ces caractères. Les caractères spéciaux sont les suivants :%, @, &, $, #, \*, :, ;, ., **,** , !, ?, \<, >, +, =, ^, ~, |, \\, /, (, ), [, ], {, }, “, et ‘.  
  
## <a name="data-types"></a>Types de données  
 La transformation de recherche de terme ne peut utiliser qu'une colonne contenant le type de données DT_WSTR ou DT_NTEXT. Si une colonne contient du texte, mais pas l'un de ces types de données, la transformation de conversion de données peut ajouter une colonne avec le type de données DT_WSTR ou DT_NTEXT au flux de données, puis copier les valeurs de la colonne dans cette nouvelle colonne. La sortie de la transformation de conversion de données peut ensuite être utilisée comme entrée de la transformation de recherche de terme. Pour plus d’informations, voir [Data Conversion Transformation](data-conversion-transformation.md).  
  
## <a name="configuration-the-term-lookup-transformation"></a>Configuration de la transformation de recherche de terme  
 Les colonnes d’entrée de la transformation de recherche de terme incluent la propriété InputColumnType, qui indique l’utilisation de la colonne. InputColumnType peut contenir les valeurs ci-dessous :  
  
-   La valeur 0 indique que la colonne est transmise à la sortie uniquement et n'est pas utilisée dans la recherche.  
  
-   La valeur 1 indique que la colonne est utilisée dans la recherche uniquement.  
  
-   La valeur 2 indique que la colonne est transmise à la sortie et est utilisée dans la recherche.  
  
 Les colonnes de sortie de la transformation, dont la propriété InputColumnType a la valeur 0 ou 2, sont accompagnées de la propriété CustomLineageID, qui contient l’identificateur de lignage affecté à la colonne par un composant amont du flux de données.  
  
 La transformation de recherche de terme ajoute deux colonnes à la sortie de transformation, nommée par défaut `Term` et `Frequency`. `Term` contient un terme issu de la table de recherche et `Frequency` contient le nombre d'occurrences du terme de la table de référence dans le jeu de données d'entrée. Ces colonnes n’incluent pas la propriété CustomLineageID.  
  
 La table de recherche doit être une table d'une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou Access. Si la sortie de la transformation d'extraction de terme est enregistrée dans une table, cette table peut être utilisée comme table de référence (sachant que les autres tables peuvent également être utilisées). Pour pouvoir utiliser la transformation de recherche de terme sur le texte de fichiers plats, de classeurs Excel ou d’autres sources, vous devez les importer dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou Access.  
  
 La transformation de recherche de terme utilise une connexion OLE DB distincte pour se connecter à la table de référence. Pour plus d’informations, consultez [OLE DB Connection Manager](../../connection-manager/ole-db-connection-manager.md).  
  
 La transformation de recherche de terme fonctionne en mode de mise en cache globale préalable. Au moment de l'exécution, elle lit les termes de la table de référence et les stocke dans sa mémoire privée avant de traiter toute ligne d'entrée de la transformation.  
  
 Dans la mesure où les termes d'une ligne de colonne d'entrée peuvent se répéter, la sortie de la transformation de recherche de terme contient généralement plus de lignes que l'entrée de la transformation.  
  
 La transformation comporte une entrée et une sortie. Elle ne prend pas en charge les sorties d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation de recherche de terme**, cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de Transformation de recherche de terme &#40;onglet de la Table de référence&#41;](../../term-lookup-transformation-editor-reference-table-tab.md)  
  
-   [Éditeur de Transformation de recherche de terme &#40;onglet recherche de terme&#41;](../../term-lookup-transformation-editor-term-lookup-tab.md)  
  
-   [Éditeur de Transformation de recherche de terme &#40;onglet Avancé&#41;](../../term-lookup-transformation-editor-advanced-tab.md)  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
  