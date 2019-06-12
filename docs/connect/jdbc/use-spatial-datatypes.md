---
title: À l’aide des types de données spatiales | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ce3df0755799e907bb286e10f5711a58a48135bb
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782473"
---
# <a name="using-spatial-datatypes"></a>Utilisation des types de données spatiales

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les types de données spatiales (géométrie et géographie) sont pris en charge préversion de pilote JDBC 6.5.0. Types de données spatiales ne sont actuellement pas pris en charge avec des procédures stockées, les paramètres à valeurs de Table (TVP), copie en bloc et Always Encrypted. Cette page affiche les que différents cas d’usage des types de données Geometry et Geography avec le pilote JDBC. Pour une vue d’ensemble sur les types de données spatiales, consultez [vue d’ensemble des Types de données spatiales](https://docs.microsoft.com/sql/relational-databases/spatial/spatial-data-types-overview) page.

## <a name="creating-a-geometry--geography-object"></a>Création d’une géométrie / objet géographique

Il existe deux façons de créer une géométrie / objet géographique - soit convertir à partir d’un texte connues (WKT) ou un WKB Well-Known Binary ().

### <a name="creating-from-wkt"></a>Création à partir de WKT

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

Cela créera un objet Geometry de LINESTRING avec système identificateur SRID (Spatial Reference) 0 et un objet géographique avec SRID 4326.

### <a name="creating-from-wkb"></a>Création à partir de WKB

```java
byte[] geomWKB = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogWKB = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomWKB);
Geography geogWKT = Geography.deserialize(geogWKB);
```

Cela créera un objet Geometry et Geography qui équivaut à ceux créés à partir de l’entrée WKT précédemment.

## <a name="working-with-a-geometry--geography-object"></a>Travaillez sur une géométrie / objet géographique

En supposant que l’utilisateur a une table sur SQL Server, comme ci-dessous :

```sql
CREATE TABLE sampleTable (c1 geometry)  
```

Un exemple de script pour insérer une valeur géométrique serait :

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) connection.prepareStatement("insert into sampleTable values (?)");
pstmt.setGeometry(1, geomWKT);  
pstmt.execute();
```

Le même peut être effectué pour l’équivalent de la géographie, à l’aide d’une colonne de géographie et **setGeography()** (méthode).

Pour lire une géométrie / colonne de géographie :

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

Le même peut être effectué pour l’équivalent de la géographie, à l’aide d’une colonne de géographie et **getGeography()** (méthode).

## <a name="newly-introduced-apis"></a>API nouvellement introduites

Il s’agit des nouvelle API publiques qui ont été introduites avec cet ajout, dans les classes **SQLServerPreparedStatement**, **SQLServerResultSet**, **Geometry**et  **Geography**.

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|Méthode|Description|
|:------|:----------|
|void setGeometry (int n, géométrie x)| Définit le paramètre désigné à l’objet de classe microsoft.sql.Geometry donné.
|void setGeography (int n, Geography x)| Définit le paramètre désigné à l’objet de classe microsoft.sql.Geography donné.

### <a name="sqlserverresultset"></a>SQLServerResultSet

|Méthode|Description|
|:------|:----------|
|Géométrie getGeometry (colunIndex int)| Retourne la valeur de la colonne désignée dans la ligne actuelle de cet objet de jeu de résultats en tant qu’objet com.microsoft.sqlserver.jdbc.Geometry dans le langage de programmation Java.
|Géométrie getGeometry (columnName chaîne)| Retourne la valeur de la colonne désignée dans la ligne actuelle de cet objet de jeu de résultats en tant qu’objet com.microsoft.sqlserver.jdbc.Geometry dans le langage de programmation Java.
|Geography getGeography (colunIndex int)| Retourne la valeur de la colonne désignée dans la ligne actuelle de cet objet de jeu de résultats en tant qu’objet com.microsoft.sqlserver.jdbc.Geography dans le langage de programmation Java.
|Geography getGeography (columnName chaîne)| Retourne la valeur de la colonne désignée dans la ligne actuelle de cet objet de jeu de résultats en tant qu’objet com.microsoft.sqlserver.jdbc.Geography dans le langage de programmation Java.

### <a name="geometry"></a>Geometry

|Méthode|Description|
|:------|:----------|
|STGeomFromText Geometry (wkt String, int SRID)| Constructeur pour une instance Geometry à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text), à laquelle s’ajoutent les valeurs Z (élévation) et M (mesure) apportées par l’instance.
|Geometry STGeomFromWKB(byte[] wkb)| Constructeur pour une instance Geometry à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary).
|Géométries désérialiser (byte [] wkb)| Constructeur pour une instance Geometry à partir d’un format interne SQL Server pour les données spatiales.
|Analyse de géométrie (chaîne wkt)| Constructeur pour une instance Geometry à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text). Identificateur de référence spatiale est défini par défaut sur 0.
|Point géométrique (double x, y double int SRID)| Constructeur pour une instance Geometry qui représente une instance Point à partir de ses valeurs X et Y et un identificateur de référence spatiale.
|String STAsText()| Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d’une instance Geometry. Ce texte ne contiendra aucune valeur Z (élévation) ou M (mesure) apportée par l'instance.
|byte[] STAsBinary()| Retourne la représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary) d’une instance Geometry. Cette valeur ne contiendra aucune valeur Z ou M apportée par l'instance.
|byte[] serialize()| Retourne les octets qui représentent un format interne SQL Server de type Geometry.
|hasM() booléenne| Retourne si l’objet contient une valeur M (mesure).
|hasZ() booléenne| Retourne si l’objet contient une valeur Z (élévation).
|Double getZ()| Retourne la valeur de coordonnée X.
|Double getZ()| Retourne la valeur de coordonnée Y.
|Double getZ()| Retourne la valeur M (mesure) de l’objet.
|Double getZ()| Retourne la valeur Z (élévation) de l’objet.
|int getSrid()| Retourne la valeur d’identificateur de référence spatiale (SRID).
|isNull() booléenne| Retourne si l’objet Geometry est null.
|int STNumPoints()| Retourne le nombre de points dans l’objet Geometry.
|Chaîne STGeometryType()| Retourne le nom de type OGC (Open Geospatial Consortium) représenté par une instance géométrique.
|Chaîne asTextZM()| Retourne la représentation sous forme de texte connues (WKT) de l’objet Geometry.
|ToString() de la chaîne| Retourne la représentation de chaîne de l’objet Geometry.

### <a name="geography"></a>Géographie

|Méthode|Description|
|:------|:----------|
|STGeomFromText Geography (wkt String, int SRID)| Constructeur pour une instance Geography à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text), à laquelle s’ajoutent les valeurs Z (élévation) et M (mesure) apportées par l’instance.
|Geography STGeomFromWKB(byte[] wkb)| Constructeur pour une instance Geography à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary).
|Geography deserialize(byte[] wkb)| Constructeur pour une instance Geography à partir d’un format interne SQL Server pour les données spatiales.
|Analyse de géographie (chaîne wkt)| Constructeur pour une instance Geography à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text). Identificateur de référence spatiale est défini par défaut sur 0.
|Point géographique (double lon, LAT. double, int SRID)| Constructeur pour une instance Geography qui représente une instance Point à partir de sa longitude et de sa latitude, et d’un ID de référence spatiale.
|String STAsText()| Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d’une instance Geography. Ce texte ne contiendra aucune valeur Z (élévation) ou M (mesure) apportée par l'instance.
|byte[] STAsBinary())| Retourne la représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary) d’une instance Geography. Cette valeur ne contiendra aucune valeur Z ou M apportée par l'instance.
|byte[] serialize()| Retourne les octets qui représentent un format interne SQL Server de type Geography.
|hasM() booléenne| Retourne si l’objet contient une valeur M (mesure).
|hasZ() booléenne| Retourne si l’objet contient une valeur Z (élévation).
|Double getLatitude()| Retourne la valeur de latitude.
|Double getLongitude()| Retourne la valeur de longitude.
|Double getZ()| Retourne la valeur M (mesure) de l’objet.
|Double getZ()| Retourne la valeur Z (élévation) de l’objet.
|int getSrid()| Retourne la valeur d’identificateur de référence spatiale (SRID).
|isNull() booléenne| Retourne si l’objet Geography est null.
|int STNumPoints()| Retourne le nombre de points dans l’objet Geography.
|Chaîne STGeographyType()| Retourne le nom de type OGC (Open Geospatial Consortium) représenté par une instance géographique.
|Chaîne asTextZM()| Retourne la représentation sous forme de texte connues (WKT) de l’objet Geography.
|ToString() de la chaîne| Retourne la représentation de chaîne de l’objet Geography.

## <a name="limitations-of-spatial-datatypes"></a>Limitations des types de données spatiales

1. Le sub-types de données spatiales **CircularString**, **CompoundCurve**, **CurvePolygon**, et **FullGlobe** sont uniquement pris en charge à partir de SQL Server 2012 et versions ultérieures.

2. Toujours chiffré ne peut pas être utilisé avec les types de données spatiales.

3. Procédures stockées, TVP et BulkCopy opérations ne sont actuellement pas prises en charge avec les types de données spatiales.

## <a name="see-also"></a>Voir aussi

[Exemple de types de données spatiales (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)
