---
title: Recherche de mots dans le voisinage d’autres mots avec NEAR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- word searches [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- proximity searches [full-text search]
- full-text search [SQL Server], proximity searches
- full-text queries [SQL Server], proximity
- queries [full-text search], proximity
ms.assetid: 87520646-4865-49ae-8790-f766b80a41f3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3493657fb537057f7c0ff8e126582ceb6faccc11
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63238400"
---
# <a name="search-for-words-close-to-another-word-with-near"></a>Recherche de mots dans le voisinage d'autres mots avec NEAR
  Vous pouvez utiliser un terme de proximité (NEAR) dans un prédicat [CONTAINS](/sql/t-sql/queries/contains-transact-sql) ou une fonction [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) pour rechercher des mots ou des expressions à proximité les uns des autres. Vous pouvez également spécifier le nombre maximal de termes de non-recherche qui séparent le premier et le dernier terme de recherche. De plus, vous pouvez rechercher des mots ou des expressions dans n'importe quel ordre ou dans un ordre spécifié. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend en charge l’ancien [terme de proximité générique](#Generic_NEAR), qui est maintenant déconseillé et le [terme de proximité personnalisé](#Custom_NEAR), qui est une nouveauté dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
##  <a name="Custom_NEAR"></a> Le terme de proximité personnalisé  
 Le terme de proximité personnalisé présente les nouvelles fonctions suivantes :  
  
-   Vous pouvez spécifier le nombre maximal de termes de non-recherche, ou *distance maximale*, qui sépare le premier et le dernier terme de recherche pour établir une correspondance.  
  
-   Si vous spécifiez le nombre maximal de termes, vous pouvez également spécifier l'ordre dans lequel les termes de recherche doivent figurer dans les correspondances.  
  
 Pour être une correspondance valide, une chaîne de texte doit :  
  
-   commencer par l'un des termes de recherche spécifiés et se terminer par l'un des autres termes de recherche spécifiés ;  
  
-   contenir tous les termes de recherche spécifiés ;  
  
-   le nombre de termes de non-recherche, notamment de mots vides situés entre le premier et le dernier terme de recherche, doit être inférieur ou égal à la distance maximale, si celle-ci est spécifiée.  
  
 La syntaxe de base est la suivante :  
  
 NEAR (  
  
 {  
  
 *terme_de_recherche* [,... *n* ]  
  
 |  
  
 (*terme_de_recherche* [,... *n* ]) [, < maximum_distance > [, < match_order >]]  
  
 }  
  
 )  
  
> [!NOTE]  
>  Pour plus d’informations sur la syntaxe de <terme_de_proximité_personnalisé>, consultez [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).  
  
 Par exemple, vous pourriez rechercher « John » à deux termes de distance de « Smith », comme suit :  
  
```  
CONTAINS(column_name, 'NEAR((John, Smith), 2)')  
```  
  
 Les chaînes qui correspondent sont par exemple «`John Jacob Smith`» et «`Smith, John`». La chaîne «`John Jones knows Fred Smith`» contient trois termes de non-recherche intermédiaires, donc ce n'est pas une correspondance.  
  
 Pour que les termes soient recherchés dans un ordre spécifié, vous pouvez modifier le terme de proximité de l'exemple en `NEAR((John, Smith),2, TRUE).` Cela permet de rechercher «`John`» à deux termes de distance de «`Smith`», mais uniquement à condition que «`John`» précède «`Smith`». Dans une langue qui se lit de gauche à droite, tel que l'anglais, un exemple de chaîne correspondante est`John Jacob Smith`.  
  
 Notez que pour une langue qui se lit de droite à gauche, telle que l'arabe ou l'hébreu, le moteur d'indexation et de recherche en texte intégral applique les termes spécifiés dans l'ordre inverse. De même, l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] inverse automatiquement l'ordre d'affichage des mots spécifiés dans les langues s'écrivant de droite à gauche.  
  
> [!NOTE]  
>  Pour plus d'informations, consultez «[Considérations supplémentaires concernant les recherches de proximité](#Additional_Considerations)», plus loin dans cette rubrique.  
  
### <a name="how-maximum-distance-is-measured"></a>Comment mesurer la distance maximale  
 Une distance maximale spécifique, telle que 10 ou 25, détermine combien de termes de non-recherche, notamment les mots vides, peuvent séparer le premier et le dernier terme de recherche dans une chaîne donnée. Par exemple, `NEAR((dogs, cats, "hunting mice"), 3)` retournerait la ligne suivante, dans laquelle le nombre total de termes de non-recherche est trois («`enjoy`», «`but`» et «`avoid`») :  
  
 «`Cats` `enjoy` `hunting mice``, but avoid` `dogs``.`»  
  
 Le même terme de proximité ne retournerait pas la ligne suivante, car les quatre termes de non-recherche («`enjoy`», «`but`», «`usually`» et «`avoid`») dépassent la distance maximale :  
  
 «`Cats` `enjoy` `hunting mice``, but usually avoid` `dogs``.`»  
  
### <a name="combining-a-custom-proximity-term-with-other-terms"></a>Combinaison d'un terme de proximité personnalisé avec d'autres termes  
 Vous pouvez combiner un terme de proximité personnalisé avec d'autres termes. Vous pouvez utiliser AND (&), OR (|) ou AND NOT (&!) pour combiner un terme de proximité personnalisé avec un autre terme de proximité personnalisé, un terme simple ou un terme de préfixe. Exemple :  
  
-   CONTAINS('NEAR((*terme1*,*terme2*),5) AND *terme3*')  
  
-   CONTAINS('NEAR((*terme1*,*terme2*),5) OR *terme3*')  
  
-   CONTAINS('NEAR((*terme1*,*terme2*),5) AND NOT *terme3*')  
  
-   CONTAINS('NEAR((*terme1*,*terme2*),5) AND NEAR((*terme3*,*terme4*),2)')  
  
-   CONTAINS('NEAR((*terme1*,*terme2*),5) OR NEAR((*terme3*,*terme4*),2, TRUE)')  
  
 Par exemple,  
  
```  
CONTAINS(column_name, 'NEAR((term1, term2), 5, TRUE) AND term3')  
```  
  
 Vous ne pouvez pas combiner un terme de proximité personnalisé avec un terme de proximité générique (*terme1* NEAR *terme2*), une forme canonique (ISABOUT …) ou un terme pondéré (FORMSOF …).  
  
### <a name="example-using-the-custom-proximity-term"></a>Exemple : En utilisant le terme de proximité personnalisé  
 L'exemple suivant recherche dans la table `Production.Document` de l'exemple de base de données `AdventureWorks2012` tous les résumés de document qui contiennent le mot « reflector » dans le même document que le mot « bracket ».  
  
```  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable   
INNER JOIN CONTAINSTABLE(Production.Document, Document,  
  'NEAR(bracket, reflector)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 50  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  

  
##  <a name="Additional_Considerations"></a> Considérations supplémentaires pour les recherches de proximité  
 Cette section présente des points à prendre en considération qui concernent à la fois les recherches de proximité génériques et personnalisées :  
  
-   Chevauchement des occurrences des termes de recherche  
  
     Les recherches de proximité ne cherchent toujours que des occurrences sans chevauchement. Les occurrences des termes de recherche qui se chevauchent ne sont jamais validées comme des correspondances. Par exemple, supposons le terme de proximité suivant, qui recherche «`A`» et «`AA`», dans cet ordre, à une distance maximale de deux termes :  
  
    ```  
    CONTAINS(column_name, 'NEAR((A,AA),2, TRUE')  
    ```  
  
     Les correspondances possibles sont, par exemple, «`AAA`», «`A.AA`» et «`A..AA`». Les lignes contenant simplement «`AA`» ne correspondent pas.  
  
    > [!NOTE]  
    >  Vous pouvez spécifier des termes qui se chevauchent, par exemple, `NEAR("mountain bike", "bike trails")` ou `(NEAR(comfort*, comfortable), 5)`. Spécifier des termes qui se chevauchent rend la requête plus complexe en augmentant les permutations de correspondances possibles. Si vous spécifiez un grand nombre de termes se chevauchant, la requête peut échouer en raison de ressources insuffisantes. Dans ce cas, simplifiez la requête et réessayez.  
  
-   NEAR générique et NEAR personnalisé (qu'une distance maximale soit spécifiée ou non) indiquent tous deux la distance logique entre les termes, plutôt que la distance absolue qui les sépare. Par exemple, les termes des différentes expressions ou phrases d'un paragraphe sont considérés comme plus éloignés que les termes situés dans une même expression ou phrase, indépendamment de leur proximité réelle, en supposant que leur relation soit moins étroite. De même, les termes situés dans des paragraphes différents sont considérés comme étant encore plus éloignés. Si une correspondance comprend la fin d'une phrase, d'un paragraphe ou d'un chapitre, l'intervalle utilisé pour le classement d'un document est augmenté respectivement de 8, 128 ou 1024.  
  
-   Impact des termes de proximité sur le classement par la fonction CONTAINSTABLE  
  
     Lorsque NEAR est utilisé dans la fonction CONTAINSTABLE, le nombre de résultats dans un document par rapport à sa longueur, ainsi que la distance entre le premier et le dernier terme de recherche dans chacun des résultats, affectent le classement de chaque document. Pour un terme de proximité générique, si les termes de recherche trouvés sont séparés de >50 termes logiques, le classement retourné sur un document est 0. Pour un terme de proximité personnalisé qui ne spécifie pas d'entier comme distance maximale, un document qui contient uniquement des résultats à intervalle de >100 termes logiques recevra un classement de 0. Pour plus d'informations sur le classement des recherches de proximité personnalisées, consultez [Limit Search Results with RANK](limit-search-results-with-rank.md).  
  
-   Option de serveur **Transformer les mots parasites**   
  
     La valeur de l’option **Transformer les mots parasites** influe sur la manière dont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traite les mots vides, s’ils sont spécifiés dans les recherches de proximité. Pour plus d’informations, voir [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md).  
  

  
##  <a name="Generic_NEAR"></a> Le terme de proximité générique déconseillé  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Nous vous recommandons d'utiliser le [terme de proximité personnalisé](#Custom_NEAR).  
  
 Un terme de proximité générique indique que les termes de recherche spécifiés doivent figurer dans un document pour qu’une correspondance soit retournée, indépendamment du nombre de termes de non-recherche (la *distance*) entre les termes de recherche. La syntaxe de base est la suivante :  
  
 { *terme_de_recherche* {NEAR | ~} *terme_de_recherche* } [,... *n* ]  
  
 Par exemple, dans les exemples suivants, les mots « fox » et « chicken »doivent apparaître tous les deux, dans n'importe quel ordre, pour qu'une correspondance soit établie :  
  
-   `CONTAINS(column_name, 'fox NEAR chicken')`  
  
-   `CONTAINSTABLE(table_name, column_name, 'fox ~ chicken')`  
  
> [!NOTE]  
>  Pour plus d’informations sur la syntaxe de <terme_de_proximité_générique>, consultez [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).  
  
 Pour plus d'informations, consultez «[Considérations supplémentaires concernant les recherches de proximité](#Additional_Considerations)», plus loin dans cette rubrique.  
  
### <a name="combining-a-generic-proximity-term-with-other-terms"></a>Combinaison d'un terme de proximité générique avec d'autres termes  
 Vous pouvez utiliser AND (&), OR (|) ou AND NOT (&!) pour combiner un terme de proximité générique avec un autre terme de proximité générique, un terme simple ou un terme de préfixe. Exemple :  
  
```  
CONTAINSTABLE (Production.ProductDescription,  
   Description,   
   '(light NEAR aluminum) OR  
   (lightweight NEAR aluminum)'  
)  
```  
  
 Vous ne pouvez pas combiner un terme de proximité générique avec un terme de proximité personnalisé, tel que `NEAR((term1,term2),5)`, un terme pondéré (ISABOUT …) ou un terme (FORMSOF …).  
  
### <a name="example-using-the-generic-proximity-term"></a>Exemple : En utilisant le terme de proximité générique  
 L'exemple suivant utilise le terme de proximité générique pour rechercher le mot « reflector » dans le même document que le mot « bracket ».  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable INNER JOIN  
  CONTAINSTABLE(Production.Document, Document,  
  '(reflector NEAR bracket)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
 Notez que vous pouvez aussi inverser l'ordre des termes dans CONTAINSTABLE pour obtenir le même résultat :  
  
```  
CONTAINSTABLE(Production.Document, Document, '(bracket NEAR reflector)' ) AS KEY_TBL  
```  
  
 Vous pouvez utiliser le caractère tilde (~) à la place du mot clé NEAR utilisé dans la requête précédente et obtenir les mêmes résultats :  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket)' ) AS KEY_TBL  
```  
  
 Il est possible de spécifier plusieurs mots ou expressions dans les conditions de recherche. Par exemple, il est possible d'écrire :  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket ~ installation)' ) AS KEY_TBL  
```  
  
 Cela signifie que « reflector » doit figurer dans le même document que « bracket », et que « bracket » doit figurer dans le même document que « installation ».  
  

  
## <a name="see-also"></a>Voir aussi  
 [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql)   
 [Exécuter une requête avec une recherche en texte intégral](query-with-full-text-search.md)   
 [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)  
  
  
