---
title: Données de date et d’heure
description: Décrit comment utiliser les nouveaux types de données de date et d’heure introduits dans SQL Server 2008.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 43a7f03a4e8a9a3c67a3263f792f2f921eef7a78
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928857"
---
# <a name="date-and-time-data"></a>Données de date et d’heure

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server 2008 introduit de nouveaux types de données pour gérer les informations de date et d’heure. Les nouveaux types de données incluent des types distincts pour la date et l’heure, ainsi que des types de données étendus avec une plus grande plage, une meilleure précision et la prise en compte des fuseaux horaires. Le fournisseur de données Microsoft SqlClient pour SQL Server (<xref:Microsoft.Data.SqlClient>) fournit une prise en charge complète de l'ensemble des nouvelles fonctionnalités du moteur de base de données SQL Server 2008. Vous devez installer le .NET Framework 3.5 SP1 (ou version ultérieure) ou .NET Core 1.0 (ou version ultérieure) pour utiliser ces nouvelles fonctionnalités avec SqlClient.  
  
Les versions de SQL Server antérieures à SQL Server 2008 avaient uniquement deux types de données pour travailler avec des valeurs de date et heure : `datetime` et `smalldatetime`. Ces deux types de données contiennent à la fois les valeurs de date et d’heure, ce qui rend difficile l’utilisation de l’une sans l’autre. De plus, seules les dates postérieures à l'introduction du calendrier grégorien en Angleterre en 1753 sont prises en charge par ces types. Une autre limitation est que ces types de données plus anciens ne prennent pas en charge les fuseaux horaires, ce qui rend difficile l’utilisation de données provenant de plusieurs fuseaux horaires.  
  
La documentation complète relative aux types de données SQL Server est disponible dans la Documentation en ligne de SQL Server. Pour plus d’informations sur les données de date et heure, consultez [Utilisation des données de date et d’heure](https://go.microsoft.com/fwlink/?LinkID=98361).
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Types de données date/heure introduits dans SQL Server 2008  
 Le tableau suivant décrit les nouveaux types de données de date et heure.  
  
|Type de données SQL Server|Description|  
|--------------------------|-----------------|  
|`date`|Le type de données `date` est situé dans une plage comprise entre le 1er janvier 01 et le 31 décembre 9999, avec une précision d’un jour. La valeur par défaut est 1er janvier 1900. La taille de stockage est de 3 octets.|  
|`time`|Le type de données `time` stocke les valeurs d’heure uniquement en fonction d’une horloge au format 24 heures. Le type de données `time` est compris entre 00:00:00.0000000 et 23:59:59.9999999 avec une précision de 100 nanosecondes. La valeur par défaut est 00:00:00.0000000 (minuit). Le type de données `time` prend en charge une précision à la fraction de seconde, et la taille de stockage varie entre trois et six octets, en fonction de la précision spécifiée.|  
|`datetime2`|Le type de données `datetime2` associe la plage et la précision des types de données `date` et `time` en un seul type.<br /><br /> Les valeurs par défaut et les formats de littéral de chaîne sont les mêmes que ceux définis dans les types de données `date` et `time`.|  
|`datetimeoffset`|Le type de données `datetimeoffset` présente toutes les fonctionnalités du type de données `datetime2` avec en plus un décalage horaire. Le décalage horaire est représenté sous la forme [+&#124;-] HH:MM. HH est un nombre à deux chiffres, compris entre 00 et 14, qui représente le nombre d’heures dans le décalage de fuseau horaire. MM est un nombre à deux chiffres, compris entre 00 et 59, qui représente le nombre de minutes supplémentaires dans le décalage de fuseau horaire. Les formats d’heure sont pris en charge jusqu’à une précision de 100 nanosecondes. Le signe obligatoire + ou- indique si le décalage de fuseau horaire est ajouté ou soustrait à l’heure UTC (temps universel coordonné, ou heure moyenne de Greenwich) pour obtenir l’heure locale.|  
  
> [!NOTE]
>  Pour plus d’informations sur l’utilisation du mot clé `Type System Version`, consultez <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Format de date et ordre des dates  
La façon dont SQL Server analyse les valeurs de date et heure dépend non seulement de la version du système de type et de la version du serveur, mais également des paramètres de format et de langue par défaut du serveur. Une chaîne de date qui fonctionne pour les formats de date d’une langue peut ne pas être reconnaissable si la requête est exécutée par une connexion qui utilise des paramètres de format de date et de langue différents.  
  
L’instruction Transact-SQL SET LANGUAGE définit implicitement le DATEFORMAT qui détermine l’ordre des parties de la date. Vous pouvez utiliser l’instruction Transact-SQL SET DATEFORMAT sur une connexion pour lever l’ambiguïté des valeurs de date en classant les parties de la date dans l’ordre MJA, JMA, AMJ, AJM, MAJ ou JAM.  
  
Si vous ne spécifiez pas de DATEFORMAT pour la connexion, SQL Server utilise la langue par défaut associée à la connexion. Par exemple, une chaîne de date « 01/02/03 » est interprétée comme MJA (2 janvier 2003) sur un serveur avec un paramètre de langue Anglais des États-Unis, et comme JMA (1er février 2003) sur un serveur dont le paramètre de langue est Anglais britannique. L’année est déterminée à l’aide de la règle d’année de troncature de SQL Server, qui définit la date de troncature pour l’affectation de la valeur de siècle. Pour plus d’informations, consultez [Option Année de coupure à deux chiffres](https://go.microsoft.com/fwlink/?LinkId=120473) dans la Documentation en ligne de SQL Server.  
  
> [!NOTE]
>  Le format de date AJM n’est pas pris en charge lors de la conversion d’un format de chaîne en `date`, `time`, `datetime2` ou `datetimeoffset`.  
  
Pour plus d’informations sur la manière dont SQL Server interprète les données de date et d’heure, consultez [Utilisation des donnée de date et d’heure](https://go.microsoft.com/fwlink/?LinkID=98361) dans la Documentation en ligne de SQL Server 2008.  
  
## <a name="datetime-data-types-and-parameters"></a>Paramètres et types de données de date et heure  
Les énumérations suivantes ont été ajoutées à <xref:System.Data.SqlDbType> pour prendre en charge les nouveaux types de données de date et heure.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Vous pouvez spécifier le type de données d’un objet <xref:Microsoft.Data.SqlClient.SqlParameter> à l’aide de l’une des énumérations <xref:System.Data.SqlDbType> précédentes. 

> [!NOTE]
> Vous ne pouvez pas définir la propriété `DbType` d’un `SqlParameter` sur `SqlDbType.Date`.

Vous pouvez également spécifier le type d’un objet <xref:Microsoft.Data.SqlClient.SqlParameter> de manière générique en attribuant à la propriété <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A> d’un objet `SqlParameter` une valeur d’énumération <xref:System.Data.DbType> particulière. Les valeurs d’énumération suivantes ont été ajoutées à l’objet <xref:System.Data.DbType> pour prendre en charge les types de données `datetime2` et `datetimeoffset` :  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
Ces nouvelles énumérations complètent les énumérations `Date`, `Time` et `DateTime`.  
  
Le type de fournisseur de données Microsoft SqlClient d’un objet de paramètre est déduit à partir du type .NET de la valeur de l’objet de paramètre, ou à partir du `DbType` de l’objet de paramètre. Aucun nouveau type de données <xref:System.Data.SqlTypes> n’a été introduit pour prendre en charge les nouveaux types de données de date et heure. Le tableau suivant décrit les mappages entre les types de données de date et heure SQL Server 2008 et les types de données CLR.  
  
|Type de données SQL Server|Type .NET|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Date|System.DateTime|Date|Date|  
|time|System.TimeSpan|Temps|Temps|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|DATETIME|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Propriétés de SqlParameter  
 Le tableau suivant décrit les propriétés de `SqlParameter` qui sont pertinentes pour les types de données de date et heure.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.IsNullable%2A>|Obtient ou définit une valeur indiquant si une valeur peut accepter la valeur null. Lorsque vous envoyez une valeur de paramètre null au serveur, vous devez spécifier <xref:System.DBNull> plutôt que `null` (`Nothing` en Visual Basic). Pour plus d’informations sur les valeurs Null de base de données, consultez [Gestion des valeurs null](handle-null-values.md).|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Precision%2A>|Obtient ou définit le nombre maximal de chiffres utilisés pour représenter la valeur. Ce paramètre est ignoré pour les types de données de date et heure.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Scale%2A>|Obtient ou définit le nombre de décimales à laquelle la partie heure de la valeur est résolue pour `Time`, `DateTime2`, et `DateTimeOffset`. La valeur par défaut est 0, ce qui signifie que l’échelle réelle est déduite de la valeur et envoyée au serveur.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Ignoré pour les types de données de date et heure.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Obtient ou définit la valeur du paramètre.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Obtient ou définit la valeur du paramètre.|  
  
> [!NOTE]
>  Les valeurs d’heure inférieures à zéro ou supérieures ou égales à 24 heures lèvent une <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Création de paramètres  
Vous pouvez créer un objet <xref:Microsoft.Data.SqlClient.SqlParameter> à l’aide de son constructeur ou en l’ajoutant à une collection <xref:Microsoft.Data.SqlClient.SqlCommand>.<xref:Microsoft.Data.SqlClient.SqlCommand.Parameters%2A> en appelant la méthode `Add` de la <xref:Microsoft.Data.SqlClient.SqlParameterCollection>. La méthode `Add` prendra comme entrée les arguments de constructeur ou un objet de paramètre existant.  
  
Les sections suivantes de cette rubrique fournissent des exemples de spécification des paramètres de date et heure.
  
### <a name="date-example"></a>Exemple Date  
Le fragment de code suivant montre comment spécifier un paramètre `date`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
### <a name="time-example"></a>Exemple Time  
Le fragment de code suivant montre comment spécifier un paramètre `time`.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Exemple Datetime2  
Le fragment de code suivant montre comment spécifier un paramètre `datetime2` avec les parties date et heure.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>Exemple DateTimeOffSet  
Le fragment de code suivant montre comment spécifier un paramètre `DateTimeOffSet` avec une date, une heure et un décalage de fuseau horaire égal à 0.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
Vous pouvez également fournir des paramètres à l’aide de la méthode `AddWithValue` d’une <xref:Microsoft.Data.SqlClient.SqlCommand>, comme indiqué dans le fragment de code suivant. Toutefois, la méthode `AddWithValue` ne vous permet pas de spécifier le <xref:Microsoft.Data.SqlClient.SqlParameter.DbType%2A> ou <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> pour le paramètre.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
Le paramètre `@date` peut mapper à un type de données `date`, `datetime` ou `datetime2` sur le serveur. Lorsque vous utilisez les nouveaux types de données `datetime`, vous devez définir explicitement la propriété <xref:System.Data.SqlDbType> du paramètre sur le type de données de l’instance. L’utilisation de <xref:System.Data.SqlDbType.Variant> ou la spécification implicite de valeurs de paramètres peut entraîner des problèmes de compatibilité descendante avec les types de données `datetime` et `smalldatetime`.  
  
Le tableau suivant indique quels `SqlDbTypes` sont déduits de quels types CLR :  
  
|Type CLR|SqlDbType déduit|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Récupération des données de date et d’heure  
Le tableau suivant décrit les méthodes utilisées pour récupérer des valeurs de date et d’heure SQL Server 2008.  
  
|Méthode SqlClient|Description|  
|----------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Récupère la valeur de colonne spécifiée sous la forme d’une structure <xref:System.DateTime>.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Récupère la valeur de colonne spécifiée sous la forme d’une structure <xref:System.DateTimeOffset>.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Renvoie le type qui est le type spécifique au fournisseur sous-jacent pour le champ. Renvoie les mêmes types que `GetFieldType` pour les types de date et d’heure.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Récupère la valeur de la colonne spécifiée. Renvoie les mêmes types que `GetValue` pour les nouveaux types de date et d’heure.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Récupère les valeurs dans le tableau spécifié.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Récupère la valeur de colonne en tant que <xref:System.Data.SqlTypes.SqlString>. Une <xref:System.InvalidCastException> se produit si les données ne peuvent pas être exprimées sous la forme d’une chaîne `SqlString`.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Récupère les données de colonne comme `SqlDbType` par défaut. Renvoie les mêmes types que `GetValue` pour les nouveaux types de date et d’heure.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Récupère les valeurs dans le tableau spécifié.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetString%2A>|Récupère la valeur de colonne sous forme de chaîne si la version de système de type a la valeur SQL Server 2005. Une <xref:System.InvalidCastException> se produit si les données ne peuvent pas être exprimées sous la forme d’une chaîne.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Récupère la valeur de colonne spécifiée sous la forme d’une structure <xref:System.TimeSpan>.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>|Récupère la valeur de colonne spécifiée en tant que type CLR sous-jacent.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>|Récupère des valeurs de colonne dans un tableau.|  
|<xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Retourne un élément <xref:System.Data.DataTable> qui décrit les métadonnées du jeu de résultats.|  
  
> [!NOTE]
>  Les nouveaux `SqlDbTypes` de date et heure ne sont pas pris en charge pour le code qui s’exécute in-process dans SQL Server. Une exception est levée si un de ces types est passé au serveur.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Spécification de valeurs de date et heure en tant que littéraux  
Vous pouvez spécifier des types de données de date et heure à l’aide d’un large éventail de formats de chaînes littérales, que SQL Server évalue ensuite au moment de l’exécution, en les convertissant en structures de date/heure internes. SQL Server reconnaît les données de date et heure placées entre guillemets simples ('). Les exemples ci-dessous illustrent certains formats :  
  
- Formats de date alphabétiques, tels que `'October 15, 2006'`.  
  
- Formats de date numériques, tels que `'10/15/2006'`.  
  
- Les formats de chaîne non séparés, par exemple `'20061015'`, qui serait interprété comme le 15 octobre 2006 si vous utilisiez le format de date standard ISO.  
  
> [!NOTE]
>  Vous trouverez une documentation complète pour tous les formats de chaînes littérales et d’autres fonctionnalités des types de données de date et heure dans la Documentation en ligne de SQL Server.  
  
Les valeurs d’heure inférieures à zéro ou supérieures ou égales à 24 heures lèvent une <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Ressources dans la documentation en ligne de SQL Server 2008  
Pour plus d’informations sur l’utilisation des valeurs de date et heure dans SQL Server 2008, consultez les ressources suivantes dans la Documentation en ligne de SQL Server 2008.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Types de données et fonctions de date et d’heure (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Fournit une vue d’ensemble de tous les types de données et fonctions de date et d’heure Transact-SQL.|  
|[Utilisation des données de date et d’heure](https://go.microsoft.com/fwlink/?LinkId=98361)|Fournit des informations sur les fonctions et types de données de date et d’heure, ainsi que des exemples d’utilisation.|  
|[Types de données (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|Décrit les types de données système dans SQL Server 2008.|  
  
## <a name="next-steps"></a>Étapes suivantes
- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
