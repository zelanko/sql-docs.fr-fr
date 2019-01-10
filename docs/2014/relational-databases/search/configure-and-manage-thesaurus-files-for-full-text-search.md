---
title: Configurer et gérer les fichiers de dictionnaire des synonymes pour la recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], configuring
- thesaurus [full-text search]
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5089aaa229f77c6f0012f4ceae0d5d1b17a9c11a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52792261"
---
# <a name="configure-and-manage-thesaurus-files-for-full-text-search"></a>Configurer et gérer les fichiers de dictionnaire des synonymes pour la recherche en texte intégral
  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les requêtes de texte intégral peuvent rechercher les synonymes des termes spécifiés par l'utilisateur grâce à un dictionnaire des synonymes. Un *dictionnaire des synonymes* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définit un jeu de synonymes pour une langue spécifique. Les administrateurs système peuvent définir deux formes de synonymes : les jeux d'expansion et les jeux de remplacement. En développant un dictionnaire des synonymes adapté à vos données de texte intégral, vous pouvez élargir efficacement l'étendue des requêtes de texte intégral sur ces données. La mise en correspondance avec le dictionnaire des synonymes intervient pour toutes les requêtes [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) et [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) et pour les requêtes [CONTAINS](/sql/t-sql/queries/contains-transact-sql) et [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) qui spécifient la clause FORMSOF THESAURUS.  
  
##  <a name="tasks"></a> Tâches de base pour la configuration d’un fichier de dictionnaire des synonymes  
 Pour que vos requêtes de recherche en texte intégral sur votre instance de serveur puissent rechercher les synonymes dans une langue donnée, vous devez au préalable définir des mappages de dictionnaire des synonymes pour cette langue. Chaque dictionnaire des synonymes doit être configuré manuellement de façon à définir les éléments suivants :  
  
-   Paramètre de signes diacritiques  
  
     Pour un dictionnaire des synonymes donné, tous les modèles de recherche sont sensibles ou insensibles aux signes diacritiques comme un tilde (**~**), marque d’accent aigu (**??** ), ou des trémas (**??** ) (autrement dit, *especter les accents* ou *respect des accents, non-respect de*). Par exemple, supposons que vous spécifiez le modèle « caf ?? » à remplacer par d’autres modèles dans une requête de recherche en texte intégral. Si le dictionnaire des synonymes sont non-respect des accents, recherche en texte intégral remplace le modèles « caf ?? » et « CAFE ». Si le dictionnaire des synonymes respecte les accents, recherche en texte intégral remplace seulement le modèle « caf ?? ». Par défaut, un dictionnaire des synonymes ne tient pas compte des accents.  
  
-   Jeu d'expansion  
  
     Un jeu d'expansion contient un groupe de synonymes, tels que « writer », « author » et « journalist », qui sont substitués les uns aux autres par une requête de texte intégral. Les requêtes qui contiennent une correspondance pour un synonyme dans un jeu d'expansion sont développées de manière à inclure tous les autres synonymes du jeu d'expansion.  
  
     Pour plus d'informations, consultez « Structure XML d'un jeu d'expansion », plus loin dans cette rubrique.  
  
-   Jeu de remplacement  
  
     Un jeu de remplacement contient un modèle de texte à remplacer par un jeu de substitution. Reportez-vous à l'exemple de la section « Structure XML d'un jeu de remplacement », plus loin dans cette rubrique.  
  
  
##  <a name="initial_thesaurus_files"></a> Contenu initial des fichiers de dictionnaire des synonymes  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit un fichier de dictionnaire des synonymes XML par langue prise en charge. Ces fichiers sont essentiellement vides. Ils contiennent uniquement la structure XML de niveau supérieur commune à tous les dictionnaires des synonymes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un exemple commenté de dictionnaire des synonymes.  
  
 Les fichiers de dictionnaires des synonymes fournis avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiennent tous le code XML suivant :  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
  
##  <a name="location"></a> Emplacement des fichiers de dictionnaire des synonymes  
 L'emplacement par défaut des fichiers de dictionnaires des synonymes est :  
  
 *< SQL_Server_data_files_path >* \MSSQL12. MSSQLSERVER\MSSQL\FTDATA\  
  
 Cet emplacement par défaut contient les fichiers suivants :  
  
-   Fichiers de dictionnaires des synonymes spécifiques à chaque langue  
  
     Pendant l'installation, les fichiers des dictionnaires des synonymes vides sont installés à l'emplacement précité. Un fichier distinct est fourni pour chaque langue prise en charge. Ces fichiers peuvent être personnalisés par un administrateur système.  
  
     Les noms de fichier par défaut des fichiers des dictionnaires des synonymes utilisent le format suivant :  
  
     « ts » + \<trois lettres abréviation-langue > + « .xml »  
  
     Le nom du fichier du dictionnaire des synonymes d’une langue donnée est spécifié dans le Registre, dans la valeur HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<nom-instance>\MSSearch\\<abréviation-langue>.  
  
-   Fichier du dictionnaire des synonymes global  
  
     Un fichier de dictionnaire des synonymes global vide, tsGlobal.xml.  
  
 Vous pouvez modifier l'emplacement et le nom d'un fichier de dictionnaire des synonymes en modifiant sa clé de Registre. Pour chaque langue, l'emplacement du fichier de dictionnaire des synonymes est spécifié dans la valeur de Registre suivante :  
  
 HKLM/SOFTWARE/Microsoft/Microsoft SQL Server /\<nom de l’instance>/MSSearch/Language/\<abréviation-langue > / /tsaurusfile  
  
 Le fichier du dictionnaire des synonymes global correspond à la langue « neutre », avec le LCID 0. Cette valeur ne peut être modifiée que par des administrateurs.  
  
  
##  <a name="how_queries_use_tf"></a> Fonctionnement des fichiers de dictionnaires des synonymes des requêtes  
 Une requête de dictionnaire des synonymes utilise à la fois le dictionnaire des synonymes spécifique à la langue et le dictionnaire des synonymes global. En premier lieu, la requête recherche le fichier spécifique à la langue et le charge en vue du traitement (à moins qu'il ne soit déjà chargé). La requête est développée pour inclure les synonymes spécifiques à la langue spécifiés par les règles de jeu d'expansion et de jeu de remplacement définies dans le fichier du dictionnaire des synonymes. Ces étapes sont ensuite répétées pour le dictionnaire des synonymes global. Toutefois, si un terme fait déjà partie d'une correspondance dans le fichier du dictionnaire des synonymes spécifique à la langue, ce terme est inéligible pour la mise en correspondance dans le dictionnaire des synonymes global.  
  
  
##  <a name="structure"></a> Présentation de la Structure d’un fichier de dictionnaire des synonymes  
 Chaque fichier de dictionnaire des synonymes définit un conteneur XML dont l’ID est `Microsoft Search Thesaurus` et un commentaire, `<!--` ... `-->`, qui contient un exemple de dictionnaire des synonymes. Le dictionnaire des synonymes sont défini dans un \<dictionnaire des synonymes > élément qui contient des exemples des éléments enfants qui définissent le paramètre de signes diacritiques, les jeux d’expansion et les jeux de remplacement, comme suit :  
  
-   Structure XML du paramètre de signes diacritiques  
  
     Le paramètre de signes diacritiques d'un dictionnaire des synonymes est spécifié dans un élément <diacritics_sensitive> unique. Cet élément contient une valeur entière qui contrôle le respect des accents, comme suit :  
  
    |Paramètre de signes diacritiques|Value|XML|  
    |------------------------|-----------|---------|  
    |ne respectent pas les accents|0|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |respectent les accents|1|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  Ce paramètre ne peut être appliqué qu'une seule fois dans le fichier et s'applique à tous les modèles de recherche au sein du fichier. Vous ne pouvez pas définir ce paramètre pour des modèles individuels.  
  
-   Structure XML d'un ensemble d'expansion  
  
     Chaque jeu d’expansion est compris dans un \<expansion > élément. Dans cet élément, vous spécifiez une ou plusieurs substitutions dans un \<sub > élément. Dans le jeu d'expansion, vous pouvez spécifier un groupe de substitutions synonymes les unes des autres.  
  
     Par exemple, vous pouvez modifier la section expansion pour traiter les substitutions « writer », « author » et « journalist » en tant que synonymes. Les requêtes de recherche en texte intégral contenant des correspondances dans une substitution sont étendues pour inclure toutes les autres substitutions spécifiées dans le jeu d'expansion. Par conséquent, dans l'exemple précédent, lorsque vous émettez une requête FORMS OF THESAURUS ou FREETEXT pour le mot « author », la recherche en texte intégral renvoie également les résultats contenant les mots « writer » et « journalist ».  
  
     Voici à quoi ressemble la section du jeu d'expansion pour l'exemple ci-dessus :  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   Structure XML d'un jeu de remplacement  
  
     Chaque jeu de remplacement est compris dans un \<remplacement > élément. Dans cet élément, vous pouvez spécifier un ou plusieurs modèles dans un \<pat > élément et zéro ou plusieurs substitutions dans \<sub > éléments, un par synonyme. Vous pouvez spécifier un modèle de texte à remplacer par un jeu de substitution. Les modèles et les substitutions peuvent contenir un mot ou une suite de mots. L'absence de spécification d'une substitution pour un modèle a pour effet de supprimer le modèle de la requête de l'utilisateur.  
  
     Par exemple, supposons que vous souhaitez remplacer les requêtes pour le motif « Win8 » par les substitutions « Windows Server 2012 » ou « Windows 8.0 ». Si vous exécutez une requête de texte intégral pour « Win8 », la recherche en texte intégral renvoie seulement les résultats contenant « Windows Server 2012 » ou « Windows 8.0 ». Elle ne renvoie pas les résultats contenant « Win8 ». Cela est dû au fait que le motif « Win8 » a été « remplacé » par les motifs « Windows Server 2012 » et « Windows 8.0 ».  
  
     Voici à quoi ressemble la section du jeu de remplacement pour l'exemple ci-dessus :  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     Si deux jeux de remplacement contiennent des motifs similaires en correspondance, le plus long des deux a priorité. Par exemple, si vous exécutez une requête FORMS OF THESAURUS pour « Internet Explorer online community » avec les jeux de remplacement suivants, le jeu de remplacement « Internet Explorer » est prioritaire par rapport au jeu de remplacement « Internet ». La requête sera donc traitée comme « IE online community » ou « IE 9 online community ».  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     et  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
  
##  <a name="working_with_thesaurus_files"></a> Utilisation des fichiers de dictionnaire des synonymes  
 **Pour modifier un fichier de dictionnaire des synonymes**  
  
-   [Modification d’un fichier de dictionnaire des synonymes](#editing)  
  
 **Pour charger un fichier de dictionnaire des synonymes mis à jour**  
  
-   [sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
 **Pour afficher le résultat de la création de jetons d’une combinaison d’analyseur lexical, de dictionnaire des synonymes et de liste de mots vides**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="editing"></a> Modification d’un fichier de dictionnaire des synonymes  
 Le dictionnaire des synonymes d'une langue donnée peut être configuré en modifiant son fichier XML. Pendant l’installation, vider les fichiers de dictionnaire des synonymes contenant uniquement le \<xml > conteneur et un exemple commenté \<dictionnaire des synonymes > élément sont installés. Les requêtes de recherche en texte intégral qui recherchent des synonymes fonctionnent correctement, vous devez créer une réelle \<dictionnaire des synonymes > élément qui définit un jeu de synonymes. Vous pouvez définir deux formes de synonymes : les jeux d'expansion et les jeux de remplacement.  
  
 **Restrictions pour les fichiers de dictionnaire des synonymes**  
  
 Les restrictions suivantes s'appliquent à la modification d'un fichier de dictionnaire des synonymes :  
  
-   Seuls des administrateurs système peuvent mettre à jour, modifier ou supprimer des fichiers de dictionnaire des synonymes.  
  
-   Lorsque vous modifiez des fichiers de dictionnaire des synonymes à l'aide des outils d'édition de texte, les fichiers doivent être enregistrés au format Unicode et des marques d'ordre d'octets doivent être spécifiées.  
  
-   Les entrées du dictionnaire des synonymes ne doivent pas être vides et la césure des mots ne doit pas résulter en une chaîne vide.  
  
-   Les expressions du fichier de dictionnaire des synonymes ne doivent pas dépasser 512 caractères.  
  
-   Un dictionnaire des synonymes ne doivent pas contenir d’entrées en double parmi les \<sub > entrées des jeux d’expansion et les \<pat > éléments des jeux de remplacement.  
  
 **Recommandations pour les fichiers de dictionnaire des synonymes**  
  
 Nous vous recommandons de ne pas utiliser de caractères spéciaux dans les entrées d'un fichier de dictionnaire des synonymes. En effet, le comportement des analyseurs lexicaux en ce qui concerne les caractères spéciaux est particulier. Si une entrée de dictionnaire des synonymes contient des caractères spéciaux, les analyseurs lexicaux utilisés en association avec cette entrée peuvent avoir des conséquences comportementales subtiles pour une requête de texte intégral.  
  
 Nous vous recommandons \<sub > entrées ne contiennent aucun mots vides dans la mesure où les mots vides sont omis de l’index de recherche en texte intégral. Les requêtes sont étendues pour inclure le \<sub > entrées à partir d’un fichier de dictionnaire des synonymes et si un \<sub > contient des mots vides, la taille de la requête augmente inutilement.  
  
#### <a name="to-edit-a-thesaurus-file"></a>Pour modifier un fichier de dictionnaire des synonymes  
  
1.  Ouvrez le fichier de dictionnaire des synonymes dans le Bloc-notes.  
  
2.  Si vous modifiez le fichier de dictionnaire des synonymes pour la première fois, supprimez les lignes de commentaires suivantes au début et à la fin du fichier :  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  Ajoutez, modifiez ou supprimez un jeu de remplacement ou un jeu d'expansion.  
  
4.  Enregistrez le fichier et fermez le Bloc-notes.  
  
5.  Utilisez [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) pour charger le contenu du fichier du dictionnaire des synonymes dans tempdb, en spécifiant l’identificateur de paramètres régionaux (LCID) qui correspond à la langue du fichier. Par exemple, pour le fichier du dictionnaire des synonymes anglais, tsenu.xml, le LCID correspondant est 1033.  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
  
## <a name="see-also"></a>Voir aussi  
 [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql)   
 [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql)   
 [Recherche en texte intégral](full-text-search.md)  
  
  
