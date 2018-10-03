---
title: Créer des instances de données XML | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- type casting string instances [XML in SQL Server]
- XML [SQL Server], typed
- xml data type [SQL Server], generating instances
- casting string instances [XML in SQL Server]
- typed XML
- generating XML instances [SQL Server]
- XML [SQL Server], generating instances
- white space [XML in SQL Server]
ms.assetid: dbd6c06f-db6e-44a7-855a-6a55bf374907
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8dea24689dc1dad9836c6ef2a53cf5e40f078c47
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077129"
---
# <a name="create-instances-of-xml-data"></a>Créer des instances de données XML
  Cette rubrique décrit comment générer des instances XML.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez générer des instances XML des manières suivantes :  
  
-   Conversion du type des instances de chaîne.  
  
-   Utilisation de l'instruction SELECT avec la clause FOR XML.  
  
-   Utilisation des affectations de constante.  
  
-   Utilisation du chargement en masse.  
  
## <a name="type-casting-string-and-binary-instances"></a>Conversion du type des instances binaires et de chaîne  
 Vous pouvez analyser de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chaîne des types de données, tel que [**n**] [**var**]**char**, **[n] texte**,  **varbinary**, et **image**, dans le `xml` par un cast (CAST) ou de convertir (CONVERT) la chaîne de type de données le `xml` type de données. Le code XML non typé est vérifié de façon à voir s'il est bien formé. S’il existe un schéma associé à la `xml` validation de type est également effectuée. Pour plus d’informations, consultez [Comparer du XML typé et du XML non typé](compare-typed-xml-to-untyped-xml.md).  
  
 Les documents XML peuvent être encodés à l'aide de différents encodages (par exemple, UTF-8, UTF-16, Windows 1252). Les règles définissant le comportement de l'analyseur et l'interaction entre les types de sources binaires et de chaîne avec l'encodage du document XML sont décrites ici.  
  
 Dans la mesure où le type **nvarchar** présuppose un encodage Unicode sur deux octets tel que UTF-16 ou UCS-2, l’analyseur XML traite la valeur de type chaîne comme un document ou un fragment XML encodé en Unicode sur 2 octets. Ceci signifie que le document XML doit être encodé à l'aide d'un encodage Unicode sur deux octets et être compatible avec le type de données source. Un document XML encodé en UTF-16 peut, mais ce n'est pas obligatoire, présenter un indicateur d'ordre des octets (ou BOM) UTF-16 puisque le contexte du type de source est suffisamment explicite sur le fait qu'il ne peut s'agir que d'un document encodé en Unicode sur deux octets.  
  
 Le contenu d’une chaîne de type **varchar** est traité, par l’analyseur XML, comme un fragment ou un document XML encodé sur un octet. Étant donné que la chaîne source **varchar** est associée à une page de codes, l’analyseur utilise cette page pour l’encodage si aucun code explicite n’est spécifié dans le code XML lui-même. Si une instance XML dispose d’un BOM ou d’une déclaration d’encodage, ces éléments doivent être cohérents par rapport à la page de codes sinon l’analyseur renvoie une erreur.  
  
 Le contenu du type **varbinary** est traité comme un flux CODEPOINT transmis directement à l’analyseur XML. Le document ou le fragment XML doit donc fournir le BOM ou toute autre information d'encodage incluse. L'analyseur se contente de consulter le flux pour déterminer l'encodage. Ceci signifie que le document XML encodé en UTF-16 doit fournir le BOM UTF-16 et qu'une instance sans BOM ni déclaration d'encodage est interprétée en UTF-8.  
  
 Si l’encodage du document XML n’est pas connu à l’avance et que, avant la conversion en XML, les données sont transmises comme étant de type chaîne (string) ou binaire (binary) à la place de données XML, il est recommandé de traiter les données en tant que type **varbinary**. Ainsi, quand les données d’un fichier XML sont lues par le biais de OpenRowset(), ces données à lire doivent être spécifiées comme valeur **varbinary(max)** :  
  
```  
select CAST(x as XML)   
from OpenRowset(BULK 'filename.xml', SINGLE_BLOB) R(x)  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le code XML est représenté en interne dans un format binaire encodé en UTF-16. L'encodage assuré par l'utilisateur n'est pas conservé, mais est pris en compte dans le processus d'analyse.  
  
### <a name="type-casting-clr-user-defined-types"></a>Conversion des types CLR définis par l'utilisateur  
 Si un type CLR défini par l'utilisateur présente une sérialisation XML, les instances de ce type peuvent être explicitement converties en un type de données XML. Pour obtenir des détails sur la sérialisation XML d’un type CLR défini par l’utilisateur, consultez [Sérialisation XML à partir d’objets de base de données CLR](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md).  
  
### <a name="white-space-handling-in-typed-xml"></a>Gestion des espaces blancs dans le code XML typé  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les espaces blancs figurant dans le contenu d'un élément ne sont pas significatifs s'ils se trouvent dans une séquence de données de type caractères composée uniquement d'espaces blancs délimités par des balises (balise de début ou de fin) et qu'ils ne font pas appel au codage d'entité. (Les sections CDATA sont ignorées). Ce traitement des espaces blancs se différencie de la description des espaces blancs donnée dans la spécification XML 1.0 publiée par le W3C (World Wide Web Consortium). En effet, l'analyseur XML de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne reconnaît qu'un nombre limité des sous-ensembles DTD tels qu'ils existent dans XML 1.0. Pour plus d’informations sur les sous-ensembles DTD pris en charge dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [CAST et CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
 Par défaut, l'analyseur XML rejette les espaces blancs non significatifs lors de la conversion des données chaîne en XML si l'une des conditions suivantes est vraie :  
  
-   `The xml:space` L’attribut n’est pas défini sur un élément ni sur ses éléments ancêtres.  
  
-   L'attribut `xml:space` en vigueur sur un élément, ou sur l'un de ses éléments ancêtres, a la valeur par défaut.  
  
 Exemple :  
  
```  
declare @x xml  
set @x = '<root>      <child/>     </root>'  
select @x   
```  
  
 Voici le résultat obtenu :  
  
```  
<root><child/></root>  
```  
  
 Vous pouvez toutefois modifier ce comportement. Pour conserver les espaces blancs dans une instance du type de données xml, utilisez l’opérateur CONVERT et affectez à son paramètre facultatif *style* la valeur 1. Exemple :  
  
```  
SELECT CONVERT(xml, N'<root>      <child/>     </root>', 1)  
```  
  
 Si le paramètre *style* n’est pas utilisé ou s’il a la valeur 0, les espaces non significatifs ne sont pas conservés durant la conversion de l’instance du type de données xml. Pour plus d’informations sur l’utilisation de l’opérateur CONVERT et de son paramètre *style* durant la conversion de données chaîne en instances du type de données xml, consultez [CAST et CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
### <a name="example-cast-a-string-value-to-typed-xml-and-assign-it-to-a-column"></a>Exemple : conversion d'une valeur chaîne en xml typé et affectation de cette valeur à une colonne  
 L’exemple suivant convertit une variable de chaîne qui contient un fragment XML à le `xml` type de données et puis le stocke dans la `xml` colonne de type :  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
go  
DECLARE  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
```  
  
 L’opération d’insertion suivante convertit implicitement en une chaîne à la `xml` type :  
  
```  
INSERT INTO T VALUES (3, @s)   
```  
  
 Vous pouvez explicitement cast() la chaîne à la `xml` type :  
  
```  
INSERT INTO T VALUES (3, cast (@s as xml))  
```  
  
 Vous pouvez aussi utiliser la fonction convert(), comme le montre l'exemple suivant :  
  
```  
INSERT INTO T VALUES (3, convert (xml, @s))   
```  
  
### <a name="example-convert-a-string-to-typed-xml-and-assign-it-to-a-variable"></a>Exemple : conversion d'une valeur chaîne en xml typé et affectation de cette valeur à une variable  
 Dans l’exemple suivant, une chaîne est convertie en `xml` tapez et assigné à une variable de la `xml` type de données :  
  
```  
declare @x xml  
declare  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
set @x =convert (xml, @s)  
select @x  
```  
  
## <a name="using-the-select-statement-with-a-for-xml-clause"></a>Utilisation de l'instruction SELECT avec la clause FOR XML  
 Vous pouvez utiliser la clause FOR XML dans une instruction SELECT pour renvoyer les résultats sous forme de code XML. Exemple :  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = (SELECT Column1, Column2  
               FROM   Table1, Table2  
               WHERE   Some condition  
               FOR XML AUTO)  
 ...  
```  
  
 L’instruction SELECT retourne un fragment textuel XML qui est ensuite analysé au cours de l’assignation à la `xml` variable de type de données.  
  
 Vous pouvez également utiliser le [directive TYPE](type-directive-in-for-xml-queries.md) dans la clause FOR XML qui renvoie directement à un FOR XML en tant que résultat de la requête `xml` type :  
  
```  
Declare @xmlDoc xml  
SET @xmlDoc = (SELECT ProductModelID, Name  
               FROM   Production.ProductModel  
               WHERE  ProductModelID=19  
               FOR XML AUTO, TYPE)  
SELECT @xmlDoc  
```  
  
 Voici le résultat obtenu :  
  
```  
<Production.ProductModel ProductModelID="19" Name="Mountain-100" />...  
```  
  
 Dans l’exemple suivant, le texte typé `xml` d’une requête FOR XML est inséré dans un `xml` colonne de type :  
  
```  
CREATE TABLE T1 (c1 int, c2 xml)  
go  
INSERT T1(c1, c2)  
SELECT 1, (SELECT ProductModelID, Name  
           FROM Production.ProductModel  
           WHERE ProductModelID=19  
           FOR XML AUTO, TYPE)  
SELECT * FROM T1  
go  
```  
  
 Pour plus d’informations sur FOR XML, consultez [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renvoie des instances du type de données `xml` au client comme résultat des différentes constructions serveur, telles que les requêtes FOR XML qui utilisent la directive TYPE, ou dans lesquelles le type de données `xml` est utilisé pour renvoyer du code XML d'après des colonnes, des variables et des paramètres de sortie SQL. Dans le code d’application cliente, le fournisseur ADO.NET demande que cela `xml` envoyer les informations de type de données dans un encodage binaire à partir du serveur. Toutefois, si vous utilisez FOR XML sans la directive TYPE, les données XML reviennent en tant que type chaîne. Dans tous les cas, le fournisseur client est toujours en mesure de gérer toute forme XML.  
  
## <a name="using-constant-assignments"></a>Utilisation des affectations de constante  
 Une constante de chaîne peut être utilisée pour lequel une instance de la `xml` type de données est attendu. Cela revient à convertir implicitement (via CAST) une chaîne en XML. Exemple :  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
-- Or  
SET @xmlDoc = N'<?xml version="1.0" encoding="ucs-2"?><doc/>'  
```  
  
 L’exemple précédent convertit implicitement la chaîne à la `xml` type de données et l’assigne à une `xml` variable de type.  
  
 L’exemple suivant insère une chaîne constante dans un `xml` colonne de type :  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
INSERT INTO T VALUES (3, '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>')   
```  
  
> [!NOTE]  
>  En cas de XML typé, la conformité du code XML est validée par rapport au schéma spécifié. Pour plus d’informations, consultez [Comparer du XML typé et du XML non typé](compare-typed-xml-to-untyped-xml.md).  
  
## <a name="using-bulk-load"></a>Utilisation du chargement en masse  
 La fonctionnalité améliorée [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) vous permet de charger en masse des documents XML dans la base de données. Vous pouvez en bloc charge des instances XML à partir de fichiers dans le `xml` colonnes de type dans la base de données. Pour obtenir des exemples fonctionnels, consultez [ Exemples d’importation et d’exportation en bloc de documents XML &#40;SQL Server&#41;](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md). Pour plus d’informations sur le chargement de documents XML, consultez [Charger des données XML](load-xml-data.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Récupérer et interroger des données XML](retrieve-and-query-xml-data.md)|Décrit les parties des instances XML qui ne sont pas conservées lorsqu'elles sont stockées dans des bases de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comparer du XML typé et du XML non typé](compare-typed-xml-to-untyped-xml.md)   
 [Méthodes des types de données xml](/sql/t-sql/xml/xml-data-type-methods)   
 [Langage de modification de données XML &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml)   
 [Données XML &#40;SQL Server&#41;](xml-data-sql-server.md)  
  
  
