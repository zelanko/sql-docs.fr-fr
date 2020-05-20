---
title: Changements de comportement de la recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], breaking changes
- behavior changes [full-text search]
- full-text indexes [SQL Server], breaking changes
ms.assetid: 573444e8-51bc-4f3d-9813-0037d2e13b8f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 00dc0fbda03bb7f729123a84e7e91fb2361aee9f
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2020
ms.locfileid: "83001069"
---
# <a name="behavior-changes-to-full-text-search"></a>Changements de comportement pour la recherche en texte intégral
  Cette rubrique décrit les changements de comportement de la recherche en texte intégral. Les modifications de comportement affectent le mode de fonctionnement ou d'interaction des fonctionnalités dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] par rapport aux versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="behavior-changes-in-full-text-search-in-sssql14"></a>Modifications du comportement de la recherche en texte intégral dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informations qui seront fournies par la suite.  
  
## <a name="behavior-changes-in-full-text-search-in-sssql11"></a>Modifications du comportement de la recherche en texte intégral dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] installe une nouvelle version des analyseurs lexicaux et des générateurs de formes dérivés pour l'anglais américain (LCID 1033) et l'anglais du Royaume-Uni (LCID 2057). Toutefois, vous pouvez revenir à la version précédente de ces composants si vous souhaitez conserver le comportement précédent. Pour plus d’informations, consultez [Modifier l’analyseur lexical utilisé pour l’anglais des États-Unis et l’anglais du Royaume-Uni](../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md).  
  
### <a name="new-word-breakers-and-stemmers-installed"></a>Nouveaux analyseurs lexicaux et générateurs de formes dérivées installés  
 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] met à jour les analyseurs lexicaux et générateurs de formes dérivées utilisés par la recherche en texte intégral et la recherche sémantique. Pour des raisons de cohérence entre le contenu des index et les résultats des requêtes, nous vous recommandons de réalimenter les index de recherche en texte intégral existants.  
  
1.  Il existe de nouveaux analyseurs lexicaux pour l'anglais. Si vous devez conserver le comportement antérieur, consultez [Modifier l’analyseur lexical utilisé pour l’anglais des États-Unis et l’anglais du Royaume-Uni](../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md).  
  
2.  Les analyseurs lexicaux tiers pour le danois, le polonais et le turc qui étaient inclus avec les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ont été remplacés par les composants [!INCLUDE[msCoName](../includes/msconame-md.md)] . Les nouveaux composants sont activés par défaut.  
  
3.  Il existe de nouveaux analyseurs lexicaux pour le tchèque et le grec. Les versions antérieures de la recherche en texte intégral de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne prenaient pas en charge ces deux langues.  
  
### <a name="behavior-changes-of-new-word-breakers-and-stemmers"></a>Changements de comportement des nouveaux analyseurs lexicaux et générateurs de formes dérivées  
 Les nouveaux composants peuvent retourner des résultats autres que les composants plus anciens lorsque vous remplissez et interrogez les index de recherche en texte intégral. Les tableaux suivants illustrent certaines différences pouvant se présenter dans des résultats en anglais.  
  
 Si vous devez conserver le comportement antérieur des analyseurs lexicaux et des générateurs de formes dérivées, consultez les rubriques suivantes :  
  
-   [Modifier l'analyseur lexical utilisé pour l'anglais des États-Unis et l'anglais (R.U.)](../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md)  
  
-   [Rétablir la version précédente des analyseurs lexicaux utilisés par la recherche](../relational-databases/search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)  
  
 Dans certains cas, les nouveaux composants retournent *davantage* de résultats :  
  
|**Terme**|**Résultats avec l'analyseur lexical et le générateur de formes dérivées précédents**|**Résultats avec les nouveaux analyseur lexical et générateur de formes dérivées**|  
|--------------|--------------------------------------------------------|---------------------------------------------------|  
|cat-dog|cat<br /><br /> dog|cat<br /><br /> cat-dog<br /><br /> dog|  
|cat@dog.com|cat<br /><br /> com<br /><br /> dog|cat<br /><br /> cat@dog.com<br /><br /> com<br /><br /> dog|  
|12/11/2011<br /><br /> *(où le terme est une date)*|12/11/2011<br /><br /> dd20111211|11<br /><br /> 12<br /><br /> 12/11/2011<br /><br /> 2011<br /><br /> dd20111211|  
  
 Dans certains cas, les nouveaux composants retournent des résultats *similaires* :  
  
|**Terme**|**Résultats avec l'analyseur lexical et le générateur de formes dérivées précédents**|**Résultats avec les nouveaux analyseur lexical et générateur de formes dérivées**|  
|--------------|--------------------------------------------------------|---------------------------------------------------|  
|100$|100$<br /><br /> nn100$|100$<br /><br /> nn100usd|  
|022|022<br /><br /> nn022|022<br /><br /> nn22|  
|10:49AM<br /><br /> *(où le terme est une heure)*|10:49AM<br /><br /> tt1049|10:49AM<br /><br /> tt24104900|  
  
 Dans certains cas les nouveaux composants retournent *moins* de résultats ou des résultats qui peuvent être inattendus par les applications :  
  
|**Terme**|**Résultats avec l'analyseur lexical et le générateur de formes dérivées précédents**|**Résultats avec les nouveaux analyseur lexical et générateur de formes dérivées**|  
|--------------|--------------------------------------------------------|---------------------------------------------------|  
|jěˊÿｑℭžl<br /><br /> *(où les termes ne sont pas des caractères anglais valides)*|'jěˊÿｑℭžl'|je yq zl|  
|table's|table's<br /><br /> table|table's|  
|cat-|cat<br /><br /> cat-|cat|  
|v-z *(où v et z sont des mots parasites)*|*(aucun résultat)*|v-z|  
|$100 000 USD|100 $<br /><br /> 000<br /><br /> nn000<br /><br /> nn100$<br /><br /> usd|$100 000 USD<br /><br /> nn100000usd|  
|beautiful U.S land|beautiful<br /><br /> land<br /><br /> u.s<br /><br /> us|beautiful<br /><br /> land|  
|Mt. Kent and Mt Challenger|challenger<br /><br /> kent<br /><br /> mt<br /><br /> Mt.|mt<br /><br /> kent<br /><br /> challenger|  
  
## <a name="behavior-changes-in-full-text-search-in-sql-server-2008"></a>Changements de comportement de la recherche en texte intégral dans SQL Server 2008  
 Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] et les versions ultérieures, le moteur de texte intégral est intégré en tant que service de base de données dans la base de données relationnelle dans le cadre de l’infrastructure de requête et de moteur de stockage du serveur. La nouvelle architecture de recherche en texte intégral réalise les objectifs suivants :  
  
-   Stockage et gestion intégrés : la recherche en texte intégral est désormais directement intégrée aux fonctionnalités de stockage et de gestion inhérentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , et le service MSFTESQL n’existe plus.  
  
    -   Les index de recherche en texte intégral sont stockés dans les groupes de fichiers de la base de données, et non dans le système de fichiers. Les opérations d'administration sur une base de données, telles que la création d'une sauvegarde, affectent automatiquement les index de recherche en texte intégral.  
  
    -   Un catalogue de texte intégral est maintenant un objet virtuel qui n'appartient à aucun groupe de fichiers ; c'est un concept logique qui renvoie à un groupe d'index de recherche en texte intégral. Par conséquent, de nombreuses fonctionnalités de gestion de catalogue ont été déconseillées, et cet abandon a créé des modifications avec rupture pour quelques fonctionnalités. Pour plus d’informations, consultez [fonctionnalités dépréciées de moteur de base de données dans SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md) et [modifications critiques apportées à la recherche en texte intégral](breaking-changes-to-full-text-search.md).  
  
        > [!NOTE]  
        >  [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)]Les instructions DDL  qui spécifient des catalogues de texte intégral fonctionnent correctement.  
  
-   Traitement de requêtes intégrées : le nouveau processeur de requêtes de recherche en texte intégral fait partie du Moteur de base de données et est entièrement intégré au processeur de requêtes SQL Server. Cela signifie que l'optimiseur de requête reconnaît les prédicats de requête de texte intégral et les exécute automatiquement aussi efficacement que possible.  
  
-   Administration et dépannage améliorés : la recherche en texte intégral intégrée fournit des outils pour vous aider à analyser des structures de recherche telles que l’index de recherche en texte intégral, la sortie d’un analyseur lexical donné, la configuration de mot vide, etc.  
  
-   Les mots vides et les listes de mots vides ont remplacé les mots parasites et les fichiers de mots parasites. Une liste de mots vides est un objet de base de données qui facilite les tâches gestion des mots vides et améliore l'intégrité entre instances de serveur différentes et environnements. Pour plus d’informations, consultez [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
-   [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] et les versions ultérieures contiennent de nouveaux analyseurs lexicaux pour un grand nombre des langues prises en charge par [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]. Seuls les analyseurs lexicaux pour l'anglais, le coréen, le thaï et le chinois (traditionnel et simplifié) restent inchangés. Pour les autres langues, si un catalogue de texte intégral a été importé lors de la [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] mise à niveau d’une base de données vers [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ou version ultérieure, une ou plusieurs langues utilisées par les index de recherche en texte intégral dans le catalogue de texte intégral peuvent maintenant être associées à de nouveaux analyseurs lexicaux qui peuvent se comporter légèrement différemment des analyseurs lexicaux importés. Pour plus d’informations sur la façon de garantir la cohérence entre les requêtes et le contenu de l’index de recherche en texte intégral, consultez [mise à niveau de la recherche en texte intégral](../relational-databases/search/upgrade-full-text-search.md).  
  
-   Un nouveau service de lancement FDHOST (MSSQLFDLauncher) a été ajouté. Pour plus d’informations, consultez [prise en main de la recherche en texte intégral](../relational-databases/search/get-started-with-full-text-search.md).  
  
-   L’indexation de texte intégral fonctionne avec une colonne [FileStream](../relational-databases/blob/filestream-sql-server.md) de la même façon qu’avec une `varbinary(max)` colonne. La table FILESTREAM doit avoir une colonne qui contient l'extension de nom de fichier pour chaque objet blob FILESTREAM. Pour plus d’informations, consultez [interroger avec la recherche en texte intégral](../relational-databases/search/query-with-full-text-search.md),[configurer et gérer des filtres pour la recherche](../relational-databases/search/configure-and-manage-filters-for-search.md), et [sys. fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql).  
  
     Le moteur de texte intégral indexe le contenu des objets blob FILESTREAM. L'indexation de fichiers tels que des images peut ne pas être utile. Lorsqu'un objet blob FILESTREAM est mis à jour, il est réindexé.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche en texte intégral](../relational-databases/search/full-text-search.md)   
 [Compatibilité descendante de la recherche en texte intégral](../../2014/database-engine/full-text-search-backward-compatibility.md)   
 [Mettre à niveau la recherche en texte intégral](../relational-databases/search/upgrade-full-text-search.md)   
 [Commencer à utiliser la recherche en texte intégral](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
