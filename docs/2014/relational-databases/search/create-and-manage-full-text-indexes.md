---
title: Créer et gérer des index de recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], about
ms.assetid: f8a98486-5438-44a8-b454-9e6ecbc74f83
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 164ddc7f11b37ce7b6325f177713e6d3eca8635b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054732"
---
# <a name="create-and-manage-full-text-indexes"></a>Créer et gérer des index de recherche en texte intégral
  Les informations contenues dans les index de recherche en texte intégral sont utilisées par le Moteur d'indexation et de recherche en texte intégral pour compiler des requêtes de texte intégral qui permettent de rechercher rapidement certains mots ou combinaisons de mots dans une table. Un index de recherche en texte intégral stocke les informations se rapportant aux mots significatifs et à leur emplacement dans une ou plusieurs colonnes d'une table de base de données. Un index de recherche en texte intégral est un type spécial d'index fonctionnel par jeton qui est construit et géré par le Moteur d'indexation et de recherche en texte intégral pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le processus de création d'un index de texte intégral diffère du processus de création des autres types d'index. Au lieu de construire une structure d'arbre B (B-tree) en fonction d'une valeur stockée dans une ligne particulière, le Moteur d'indexation et de recherche en texte intégral crée une structure d'index inversée, empilée, compressée et basée sur des jetons individuels provenant du texte indexé.  La taille d’un index de recherche en texte intégral est limitée uniquement par les ressources mémoire dont dispose l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute.  
  
 À compter de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], les index de recherche en texte intégral sont intégrés au Moteur de base de données, au lieu de résider dans le système de fichiers comme dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour une nouvelle base de données, le catalogue de texte intégral est désormais un objet virtuel qui n'appartient à aucun groupe de fichiers ; il s'agit tout simplement d'un concept logique qui fait référence à un groupe d'index de recherche en texte intégral. Notez toutefois que pendant la mise à niveau d’une base de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , pour tout catalogue de texte intégral qui contient des fichiers de données, un nouveau groupe de fichiers est créé ; pour plus d’informations, consultez [Mise à niveau de la fonction de recherche en texte intégral](upgrade-full-text-search.md).  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures, le moteur d'indexation et de recherche en texte intégral réside dans le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , plutôt que dans un service séparé. L'intégration du Moteur d'indexation et de recherche en texte intégral dans le Moteur de base de données permet une simplification de la gestion de l'indexation et de la recherche en texte intégral, ainsi qu'une amélioration de l'optimisation des requêtes mixtes et des performances globales.  
  
 Un seul index de recherche en texte intégral est autorisé par table. Pour qu'un index de recherche en texte intégral puisse être créé sur une table, cette dernière doit posséder une colonne d'index unique, qui n'accepte pas les valeurs Null. Vous pouvez créer un index de recherche en texte intégral sur des colonnes de type `char`, `varchar`, `nchar`, `nvarchar`, `text`, `ntext`, `image`, `xml`, `varbinary`, et `varbinary(max)` peuvent être indexées pour recherche en texte intégral. Création d’un index de recherche en texte intégral sur une colonne dont les données de type est `varbinary`, `varbinary(max)`, `image`, ou `xml` nécessite que vous spécifiez une colonne de type. Une *colonne de type* est une colonne de table dans laquelle vous stockez l’extension de fichier (.doc, .pdf, .xls, etc.) du document dans chaque ligne.  
  
 Le processus de création et de gestion d’un index de recherche en texte intégral est appelé *alimentation* (également appelé *analyse*). Il existe trois types d'alimentation de l'index de recherche en texte intégral : l'alimentation complète, l'alimentation basée sur le suivi des modifications et l'alimentation incrémentielle basée sur l'horodateur. Pour plus d’informations, consultez [Alimenter des index de recherche en texte intégral](populate-full-text-indexes.md).  
  
##  <a name="tasks"></a> Tâches courantes  
 **Pour créer un index de recherche en texte intégral**  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
 **Pour modifier un index de recherche en texte intégral**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
 **Pour supprimer un index de recherche en texte intégral**  
  
-   [DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-index-transact-sql)  
  
 [Dans cette rubrique](#top)  
  
##  <a name="structure"></a> Structure d’Index de recherche en texte intégral  
 La compréhension de la structure d'un index de recherche en texte intégral vous permet de comprendre également le fonctionnement du Moteur d'indexation et de recherche en texte intégral. Cette rubrique utilise l'extrait suivant de la table **Document** dans [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] comme exemple de table. L'extrait suivant montre deux colonnes, la colonne **DocumentID** et la colonne **Title** , ainsi que trois lignes provenant de cette table.  
  
 Pour cet exemple, il faut partir de l’hypothèse qu’un index de recherche en texte intégral a été créé sur la colonne **Title** .  
  
|DocumentID|Titre|  
|----------------|-----------|  
|1|Crank Arm and Tire Maintenance|  
|2|Front Reflector Bracket and Reflector Assembly 3|  
|3|Front Reflector Bracket Installation|  
  
 Par exemple, la table suivante, qui illustre le Fragment 1, décrit le contenu de l’index de recherche en texte intégral créé sur la colonne **Title** de la table **Document** . Les index de recherche en texte intégral contiennent plus d'informations que les éléments présentés dans cette table. La table est une représentation logique d'un index de recherche en texte intégral et est fournie à des fins de démonstration uniquement. Les lignes sont stockées dans un format compressé pour optimiser l'utilisation du disque.  
  
 Remarquez que les données ont été inversées par rapport aux documents d'origine. L'inversion se produit parce que les mots clés sont mappés aux ID de document. Pour cette raison, un index de recherche en texte intégral est souvent désigné par le nom d'un index inversé.  
  
 Remarquez également que le mot clé « and » a été supprimé de l'index de recherche en texte intégral. Cela s'explique du fait que « and » est un mot vide, et que la suppression de mots vides d'un index de recherche en texte intégral peut induire des économies substantielles en termes d'espace disque, d'où une amélioration des performances des requêtes. Pour plus d’informations sur les mots vides, consultez [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
 **Fragment 1**  
  
|Mot clé|ColId|DocId|Occurrence|  
|-------------|-----------|-----------|----------------|  
|Crank|1|1|1|  
|Arm|1|1|2|  
|Tire|1|1|4|  
|Maintenance|1|1|5|  
|Front|1|2|1|  
|Front|1|3|1|  
|Reflector|1|2|2|  
|Reflector|1|2|5|  
|Reflector|1|3|2|  
|Bracket|1|2|3|  
|Bracket|1|3|3|  
|Assembly|1|2|6|  
|3|1|2|7|  
|Installation|1|3|4|  
  
 La colonne **Keyword** contient la représentation d'un jeton unique extrait au moment de l'indexation. Les analyseurs lexicaux déterminent le contenu d'un jeton.  
  
 La colonne **ColId** contient une valeur qui correspond à une colonne particulière indexée en texte intégral.  
  
 Le `DocId` colonne contient des valeurs pour un entier sur huit octets qui est mappé à une valeur de clé de recherche en texte intégral particulière dans une table indexée en texte intégral. Ce mappage est nécessaire lorsque la clé de texte intégral n'est pas un type de données integer. Dans ce cas, les valeurs de clé des mappages entre la recherche en texte intégral et `DocId` les valeurs sont conservées dans une table séparée appelée la table de mappage DocId. Pour lancer une requête à propos de ces mappages, utilisez la procédure stockée système [sp_fulltext_keymapping](/sql/relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql) . Pour satisfaire à un critère de recherche, les valeurs DocId de la table précitée doivent être jointes avec la table de mappage DocId pour extraire des lignes de la table de base qui est interrogée. Lorsque la valeur de clé de texte intégral de la table de base est un type de données Integer, la valeur sert directement de DocId et aucun mappage n'est nécessaire. Par conséquent, l'utilisation de valeurs de clé de texte intégral Integer peut contribuer à optimiser des requêtes de texte intégral.  
  
 La colonne **Occurrence** contient une valeur entière. Pour chaque valeur DocId, il existe une liste de valeurs d'occurrences qui correspondent aux décalages de mots relatifs du mot clé spécifique contenu dans DocId. Les valeurs d'occurrences servent à déterminer les correspondances d'expressions ou de proximité, par exemple lorsque des expressions ont des valeurs d'occurrences adjacentes numériquement. Elles servent également à calculer les scores de pertinence ; par exemple, le nombre d'occurrences d'un mot clé dans DocId peut être utilisé pour l'établissement d'un score.  
  
 [Dans cette rubrique](#top)  
  
##  <a name="fragments"></a> Fragments d’Index de recherche en texte intégral  
 L'index de recherche en texte intégral logique est habituellement fractionné entre plusieurs tables internes. Chaque table interne est appelé fragment d'index de recherche en texte intégral. Quelques-uns de ces fragments peuvent contenir des données plus récentes que d'autres. Par exemple, si un utilisateur met à jour la ligne suivante dont DocId est 3 et que la table effectue un suivi automatique des modifications, un nouveau fragment est créé.  
  
|DocumentID|Titre|  
|----------------|-----------|  
|3|Rear Reflector|  
  
 Dans l'exemple suivant, qui illustre le Fragment 2, le fragment contient des données plus récentes à propos de DocId 3 par rapport à Fragment 1. Par conséquent, lorsque l'utilisateur émet des requêtes concernant « Rear Reflector », les données de Fragment 2 sont utilisées pour DocId 3. Chaque fragment est marqué avec un horodateur de création qui peut être interrogé à l’aide de la vue de catalogue [sys.fulltext_index_fragments](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql) .  
  
 **Fragment 2**  
  
|Mot clé|ColId|DocId|Occ|  
|-------------|-----------|-----------|---------|  
|Rear|1|3|1|  
|Reflector|1|3|2|  
  
 Comme on peut le constater d'après Fragment 2, les requêtes de texte intégral doivent interroger chaque fragment en interne et ignorer les entrées plus anciennes. Par conséquent, trop de fragments d'index de recherche en texte intégral dans l'index de texte intégral peut conduire à une dégradation substantielle dans les performances des requêtes. Pour réduire le nombre de fragments, réorganisez le catalogue de texte intégral en utilisant l’option REORGANIZE de l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] [ALTER FULLTEXT CATALOG](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql). Cette instruction effectue une *fusion principale*, c’est-à-dire une fusion de tous les fragments en un fragment unique plus grand, et supprime toutes les entrées obsolètes de l’index de recherche en texte intégral.  
  
 Une fois réorganisé, l'index de l'exemple contient les lignes suivantes :  
  
|Mot clé|ColId|DocId|Occ|  
|-------------|-----------|-----------|---------|  
|Crank|1|1|1|  
|Arm|1|1|2|  
|Tire|1|1|4|  
|Maintenance|1|1|5|  
|Front|1|2|1|  
|Rear|1|3|1|  
|Reflector|1|2|2|  
|Reflector|1|2|5|  
|Reflector|1|3|2|  
|Bracket|1|2|3|  
|Assembly|1|2|6|  
|3|1|2|7|  
  
 [Dans cette rubrique](#top)  
  
  
