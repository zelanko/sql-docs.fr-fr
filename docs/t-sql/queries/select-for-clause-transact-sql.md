---
title: Clause FOR (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FOR
- FOR CLAUSE
- FOR_TSQL
- FOR_CLAUSE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- XML option [SQL Server]
- BROWSE option
- FOR clause [Transact-SQL]
ms.assetid: 08a6f084-8f73-4f2a-bae4-3c7513dc99b9
caps.latest.revision: "54"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0cb4b3936aa78f22958c28351d2dad523a6d9932
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="select---for-clause-transact-sql"></a>SELECT - clause for (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Utilisez la clause FOR pour spécifier l’une des options suivantes pour les résultats de la requête.  
  
-   Autoriser les mises à jour lors de l’affichage des résultats de la requête dans un curseur de mode Parcourir en spécifiant **FOR BROWSE**.  
  
-   Format des résultats de la requête au format XML en spécifiant **FOR XML**.  
  
-   Format des résultats de la requête au format JSON en spécifiant **FOR JSON**.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[ FOR { BROWSE | <XML> | <JSON>} ]  
  
<XML> ::=  
XML   
{   
    { RAW [ ( 'ElementName' ) ] | AUTO }   
    [   
        <CommonDirectivesForXML>   
        [ , { XMLDATA | XMLSCHEMA [ ( 'TargetNameSpaceURI' ) ] } ]   
        [ , ELEMENTS [ XSINIL | ABSENT ]   
    ]  
  | EXPLICIT   
    [   
        <CommonDirectivesForXML>   
        [ , XMLDATA ]   
    ]  
  | PATH [ ( 'ElementName' ) ]   
    [  
        <CommonDirectivesForXML>   
        [ , ELEMENTS [ XSINIL | ABSENT ] ]  
    ]  
}   
  
<CommonDirectivesForXML> ::=   
[ , BINARY BASE64 ]  
[ , TYPE ]  
[ , ROOT [ ( 'RootName' ) ] ]  
  
<JSON> ::=  
JSON   
{   
    { AUTO | PATH }   
    [   
        [ , ROOT [ ( 'RootName' ) ] ]  
        [ , INCLUDE_NULL_VALUES ]  
        [ , WITHOUT_ARRAY_WRAPPER ]  
    ]  
  
}  
```  
  
## <a name="for-browse"></a>FOR BROWSE  
 BROWSE  
 Indique que des mises à jour sont autorisées pendant la consultation des données dans un curseur de mode de navigation DB-Library. Une table peut être consultée dans une application si la table comporte un **timestamp** colonne, la table comporte un index unique, et l’option FOR BROWSE se trouve à la fin des instructions SELECT envoyées à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser le \<lock_hint > HOLDLOCK dans une instruction SELECT qui comprend l’option FOR BROWSE.
  
 FOR BROWSE ne peut pas apparaître dans des instructions SELECT qui sont jointes par l'opérateur UNION.  
  
> [!NOTE]  
>  Lorsque les colonnes clés d'index unique d'une table peuvent accepter les valeurs NULL, et si la table se trouve sur le côté intérieur d'une jointure externe, l'index n'est pas pris en charge par le mode de navigation.  
  
 Le mode de navigation vous permet d'analyser les lignes de la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et d'y mettre à jour les données, une ligne après l'autre. Pour accéder à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table dans votre application en mode de navigation, vous devez utiliser une des deux options suivantes :  
  
-   L’instruction SELECT qui vous permet d’accéder aux données à partir de votre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table doit se terminer avec les mots clés **FOR BROWSE**. Lorsque vous activez le **FOR BROWSE** option à utiliser le mode de navigation, les tables temporaires sont créés.  
  
-   Vous devez exécuter ce qui suit [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction pour activer le mode de navigation à l’aide de la **NO_BROWSETABLE** option :  
  
    ```  
    SET NO_BROWSETABLE ON  
    ```  
  
     Lorsque vous activez le **NO_BROWSETABLE** option, toutes les instructions SELECT se comportent comme si le **FOR BROWSE** option est ajoutée à celles-ci. Toutefois, le **NO_BROWSETABLE** option ne pas crée les tables temporaires qui le **FOR BROWSE** option utilise généralement pour envoyer les résultats à votre application.  
  
 Lorsque vous essayez d’accéder aux données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode de navigation dans les tables à l’aide d’une requête SELECT qui implique une instruction de jointure externe, et lorsqu’un index unique est défini sur la table qui est présente sur le côté intérieur d’une instruction de jointure externe, le mode de navigation ne prend pas en charge l’index unique. Le mode de navigation prend en charge l'index unique uniquement lorsque toutes les colonnes clés d'index unique peuvent accepter les valeurs NULL. Le mode de navigation ne prend pas en charge l'index unique si les conditions suivantes sont remplies :  
  
-   Vous essayez d’accéder aux données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode de navigation dans les tables à l’aide d’une requête SELECT qui implique une instruction de jointure externe.  
  
-   Un index unique est défini sur la table qui est présente sur le côté intérieur d'une instruction de jointure externe.  
  
 Pour reproduire ce comportement en mode de navigation, procédez comme suit :  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], créez une base de données appelée SampleDB.  
  
2.  Dans la base de données SampleDB, créez une table tleft et une table tright contenant une seule colonne nommée c1. Définissez un index unique sur la colonne c1 dans la table tleft et configurez la colonne pour qu'elle accepte les valeurs NULL. Pour cela, exécutez les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes dans une fenêtre de requête appropriée :  
  
    ```  
    CREATE TABLE tleft(c1 INT NULL UNIQUE) ;  
    GO   
    CREATE TABLE tright(c1 INT NULL) ;  
    GO  
    ```  
  
3.  Insérez plusieurs valeurs dans la table tleft et la table tright. Veillez à insérer une valeur NULL dans la table tleft. Pour cela, exécutez les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes dans la fenêtre de requête :  
  
    ```  
    INSERT INTO tleft VALUES(2) ;  
    INSERT INTO tleft VALUES(NULL) ;  
    INSERT INTO tright VALUES(1) ;  
    INSERT INTO tright VALUES(3) ;  
    INSERT INTO tright VALUES(NULL) ;  
    GO  
    ```  
  
4.  Activer la **NO_BROWSETABLE** option. Pour cela, exécutez les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes dans la fenêtre de requête :  
  
    ```  
    SET NO_BROWSETABLE ON ;  
    GO  
    ```  
  
5.  Accédez aux données des tables tleft et tright en utilisant une instruction de jointure externe dans la requête SELECT. Vérifiez que la table tleft se trouve sur le côté intérieur de l'instruction de jointure externe. Pour cela, exécutez les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes dans la fenêtre de requête :  
  
    ```  
    SELECT tleft.c1   
    FROM tleft   
    RIGHT JOIN tright   
    ON tleft.c1 = tright.c1   
    WHERE tright.c1 <> 2 ;  
  
    ```  
  
     Remarquez la sortie suivante dans le volet Résultats :  
  
     c1  
  
     ---\-  
  
     NULL  
  
     NULL  
  
 Après avoir exécuté la requête SELECT pour accéder aux tables en mode de navigation, le jeu de résultats de la requête SELECT contient deux valeurs NULL pour la colonne c1 dans la table tleft à cause de la définition de l'instruction de jointure externe droite. Par conséquent, dans le jeu de résultats, vous ne pouvez pas distinguer les valeurs NULL provenant de la table de celles introduites par l'instruction de jointure externe droite. Vous pouvez recevoir des résultats incorrects si vous devez ignorer les valeurs NULL du jeu de résultats.  
  
> [!NOTE]  
>  Si les colonnes incluses dans l'index unique n'acceptent pas de valeurs NULL, toutes les valeurs NULL contenues dans le jeu de résultats ont été introduites par l'instruction de jointure externe droite.  
  
## <a name="for-xml"></a>FOR XML  
 XML  
 Spécifie que les résultats d'une requête doivent être retournés sous la forme d'un document XML. L'un des modes XML suivants doit être spécifié : RAW, AUTO, EXPLICIT. Pour plus d’informations sur les données XML et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [FOR XML &#40; SQL Server &#41; ](../../relational-databases/xml/for-xml-sql-server.md).  
  
 RAW [ **(«***ElementName***')** ]  
 Prend le résultat de la requête et transforme chaque ligne dans le jeu de résultats dans un élément XML avec un identificateur générique \<ligne / > comme balise d’élément. Vous pouvez éventuellement spécifier un nom pour l'élément de ligne. La sortie XML utilise le *ElementName* en tant qu’élément de ligne généré pour chaque ligne. Pour plus d’informations, consultez [utiliser le Mode RAW avec FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md) et [utiliser le Mode RAW avec FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 AUTO  
 Renvoie les résultats de la requête dans une arborescence XML simple et imbriquée. Chaque table dans la clause FROM, dont au moins une colonne est répertoriée dans la clause SELECT, est représentée comme un élément XML. Les colonnes listées dans la clause SELECT sont mappées vers les attributs d'éléments appropriés. Pour plus d’informations, consultez [Utiliser le mode AUTO avec FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md).  
  
 EXPLICIT  
 Spécifie que la forme de l'arborescence XML résultante est définie de manière explicite. L'utilisation de ce mode nécessite toutefois que les requêtes soient écrites d'une manière particulière, de sorte que les informations complémentaires sur l'imbrication souhaitée soient spécifiées de manière explicite. Pour plus d’informations, consultez [Utiliser le mode EXPLICIT avec FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md).  
  
 XMLDATA  
 Retourne un schéma XDR inclus, mais n'ajoute pas l'élément racine au résultat. Si XMLDATA est spécifié, le schéma XDR est ajouté au document.  
  
> [!IMPORTANT]  
>  La directive XMLDATA est déconseillée. Utilisez la génération XSD en mode RAW et AUTO. Il n'y a aucun remplacement pour la directive XMLDATA en mode EXPLICIT. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 XMLSCHEMA [ **(«***TargetNameSpaceURI***')** ]  
 Retourne le schéma XSD inclus. Lorsque vous spécifiez cette directive, vous pouvez éventuellement spécifier un URI d'espace de noms cible, qui retourne l'espace de noms spécifié dans le schéma. Pour plus d’informations, consultez [Générer un schéma XSD Inline](../../relational-databases/xml/generate-an-inline-xsd-schema.md).  
  
 ELEMENTS  
 Spécifie que les colonnes sont retournées sous la forme de sous-éléments. Sinon, elles sont mappées avec des attributs XML. Cette option est prise en charge dans les modes RAW, AUTO et PATH uniquement. Pour plus d’informations, consultez [Utiliser le mode RAW avec FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 XSINIL  
 Spécifie qu’un élément avec **xsi : nil** attribut la valeur **True** être créés pour les valeurs de colonne NULL. Cette option peut uniquement être spécifiée avec la directive ELEMENTS. Pour plus d’informations, consultez [générer des éléments pour les valeurs NULL avec le paramètre XSINIL](../../relational-databases/xml/generate-elements-for-null-values-with-the-xsinil-parameter.md).  
  
 ABSENT  
 Indique que pour les valeurs de colonne NULL, les éléments XML correspondants ne seront pas ajoutés dans le résultat XML. Vous ne devez spécifier cette option qu'avec ELEMENTS.  
  
 Chemin d’accès [ **(«***ElementName***')** ]  
 Génère un \<ligne > élément wrapper pour chaque ligne du jeu de résultats. Vous pouvez éventuellement spécifier un nom d’élément pour la \<ligne > élément wrapper. Si une chaîne vide est fournie, telles que FOR XML PATH (**''**)), un élément wrapper n’est pas généré. L'utilisation de PATH peut constituer une solution plus simple pour les requêtes écrites à l'aide de la directive EXPLICIT. Pour plus d’informations, consultez [Utiliser le mode PATH avec FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md).  
  
 BINARY BASE64  
 Spécifie que la requête retourne les données binaires au format binaire encodé base64. Cette option doit être spécifiée lors de l'extraction de données binaires en mode RAW et EXPLICIT. Cette option est utilisée par défaut en mode AUTO.  
  
 TYPE  
 Spécifie que la requête retourne les résultats en tant que **xml** type. Pour plus d’informations, consultez [Directive TYPE dans les requêtes FOR XML](../../relational-databases/xml/type-directive-in-for-xml-queries.md).  
  
 RACINE [ **(«***RootName***')** ]  
 Spécifie qu'un élément de premier niveau unique doit être ajouté au XML résultant. Vous pouvez, si vous le souhaitez, spécifier le nom d'élément racine à générer. Si le nom de racine facultatif n’est pas spécifié, la valeur par défaut \<racine > élément est ajouté.  
  
 Pour plus d’informations, consultez [FOR XML &#40; SQL Server &#41; ](../../relational-databases/xml/for-xml-sql-server.md).  
  
 **PAR exemple XML**  
  
 L'exemple suivant spécifie `FOR XML AUTO` avec les options `TYPE` et `XMLSCHEMA`. Raison de la `TYPE` option, le jeu de résultats est retourné au client comme un **xml** type. L'option `XMLSCHEMA` spécifie que le schéma XSD inclus est intégré aux données XML retournées, et l'option `ELEMENTS` spécifie que le résultat XML est centré sur les éléments.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT p.BusinessEntityID, FirstName, LastName, PhoneNumber AS Phone  
FROM Person.Person AS p  
JOIN Person.PersonPhone AS pph ON p.BusinessEntityID  = pph.BusinessEntityID  
WHERE LastName LIKE 'G%'  
ORDER BY LastName, FirstName   
FOR XML AUTO, TYPE, XMLSCHEMA, ELEMENTS XSINIL;  
```  
  
## <a name="for-json"></a>FOR JSON  
 JSON  
 Spécifiez FOR JSON pour retourner les résultats d’une requête au format texte JSON. Vous devez également spécifier un des modes de JSON suivants : AUTO ou le chemin d’accès. Pour plus d’informations sur la **FOR JSON** clause, consultez [requête résultats au Format JSON avec FOR JSON &#40; SQL Server &#41; ](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
 AUTO  
 Format de la sortie JSON automatiquement en fonction de la structure de la **sélectionnez** instruction  
            en spécifiant **FOR JSON AUTO**. Pour obtenir plus d’informations et des exemples, consultez [Mettre en forme automatiquement la sortie JSON avec le mode AUTO &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).  
  
 PATH  
 Obtenir un contrôle total sur le format de la sortie JSON en spécifiant   
            **FOR JSON PATH**. Le mode**PATH** vous permet de créer des objets wrapper et d’imbriquer des propriétés complexes. Pour obtenir plus d’informations et des exemples, consultez [Mettre en forme la sortie JSON imbriquée avec le mode PATH &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).  
  
 INCLUDE_NULL_VALUES  
 Inclure des valeurs null dans la sortie JSON en spécifiant le **INCLUDE_NULL_VALUES** option avec la **FOR JSON** clause. Si vous ne spécifiez pas cette option, la sortie n’inclut pas les propriétés JSON pour les valeurs null dans les résultats de requête. Pour plus d’informations et d’exemples, consultez [incluent les valeurs Null dans la sortie JSON avec l’Option INCLUDE_NULL_VALUES &#40; SQL Server &#41; ](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).  
  
 RACINE [ **(«***RootName***')** ]  
 Ajouter un élément de niveau supérieur unique à la sortie JSON, en spécifiant le **racine** option avec la **FOR JSON** clause. Si vous ne spécifiez pas l’option **ROOT** , la sortie JSON n'aura pas d’élément racine. Pour plus d’informations et d’exemples, consultez [ajouter un nœud racine à la sortie JSON avec l’Option ROOT &#40; SQL Server &#41; ](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
 WITHOUT_ARRAY_WRAPPER  
 Supprimer les crochets qui entourent la sortie JSON par défaut en spécifiant le **WITHOUT_ARRAY_WRAPPER** option avec la **FOR JSON** clause. Si vous ne spécifiez pas cette option, la sortie JSON sera placée entre crochets. Utilisez le **WITHOUT_ARRAY_WRAPPER** option pour générer un seul objet JSON en tant que sortie.  Pour plus d’informations, consultez [Supprimer les crochets de la sortie JSON avec l’option WITHOUT_ARRAY_WRAPPER &#40;SQL Server&#41;](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md).  
  
 Pour plus d’informations, consultez [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  
