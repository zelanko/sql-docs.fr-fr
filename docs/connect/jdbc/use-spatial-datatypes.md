---
title: Utilisation des types de données spatiaux | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f133fa066ef2c486cf7bb40c5b653c99e077bc46
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026943"
---
# <a name="using-spatial-datatypes"></a>Utilisation des types de données spatiales

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les types de données spatiaux (Geometry et Geography) sont pris en charge à partir de la version préliminaire du pilote JDBC 6.5.0. Les types de données spatiaux ne sont actuellement pas pris en charge avec les procédures stockées, les paramètres table value (TVP), BulkCopy et Always Encrypted. Cette page affiche plusieurs cas d’usage des types de données geometry et geography avec le pilote JDBC. Pour une vue d’ensemble des types de données spatiaux, consultez la page [vue d’ensemble des types de données spatiales](https://docs.microsoft.com/sql/relational-databases/spatial/spatial-data-types-overview) .

## <a name="creating-a-geometry--geography-object"></a>Création d’un objet Geometry/Geography

Il existe deux façons de créer un objet Geometry/geography: convertissez un texte bien connu (WKT) ou un binaire connu (WKB).

### <a name="creating-from-wkt"></a>Création à partir de WKT

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

Cela permet de créer un objet Geometry LINESTRING avec l’identificateur de système de référence spatial (SRID) 0 et un objet geography avec SRID 4326.

### <a name="creating-from-wkb"></a>Création à partir de WKB

```java
byte[] geomWKB = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogWKB = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomWKB);
Geography geogWKT = Geography.deserialize(geogWKB);
```

Cela créera un objet Geometry et Geography équivalent à ceux créés à partir de l’WKT précédemment.

## <a name="working-with-a-geometry--geography-object"></a>Utilisation d’un objet Geometry/Geography

En supposant que l’utilisateur dispose d’une table sur SQL Server comme ci-dessous:

```sql
CREATE TABLE sampleTable (c1 geometry)  
```

Voici un exemple de script pour insérer une valeur géométrique:

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) connection.prepareStatement("insert into sampleTable values (?)");
pstmt.setGeometry(1, geomWKT);  
pstmt.execute();
```

La même opération peut être effectuée pour la contrepartie géographique, à l’aide d’une colonne Geography et d’une méthode **setGeography ()** .

Pour lire une colonne geometry/geography:

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

La même opération peut être effectuée pour la contrepartie géographique, à l’aide d’une colonne Geography et d’une méthode **getGeography ()** .

## <a name="newly-introduced-apis"></a>API récemment introduites

Il s’agit des nouvelles API publiques introduites avec cet ajout, dans les classes **SQLServerPreparedStatement**, **SQLServerResultSet**, **Geometry**et **Geography**.

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|Méthode|Description|
|:------|:----------|
|void setGeometry (int n, Geometry x)| Définit le paramètre désigné pour l’objet de classe Microsoft. Sql. Geometry donné.
|void setGeography (int n, Geography x)| Définit le paramètre désigné pour l’objet de classe Microsoft. Sql. Geography donné.

### <a name="sqlserverresultset"></a>SQLServerResultSet

|Méthode|Description|
|:------|:----------|
|Geometry getGeometry (int colunIndex)| Retourne la valeur de la colonne désignée dans la ligne actuelle de cet objet ResultSet en tant qu’objet com. Microsoft. SqlServer. JDBC. Geometry dans le langage de programmation Java.
|Geometry getGeometry (String columnName)| Retourne la valeur de la colonne désignée dans la ligne actuelle de cet objet ResultSet en tant qu’objet com. Microsoft. SqlServer. JDBC. Geometry dans le langage de programmation Java.
|Geography getGeography (int colunIndex)| Retourne la valeur de la colonne désignée dans la ligne actuelle de cet objet ResultSet en tant qu’objet com. Microsoft. SqlServer. JDBC. Geography dans le langage de programmation Java.
|Geography getGeography (String columnName)| Retourne la valeur de la colonne désignée dans la ligne actuelle de cet objet ResultSet en tant qu’objet com. Microsoft. SqlServer. JDBC. Geography dans le langage de programmation Java.

### <a name="geometry"></a>Geometry

|Méthode|Description|
|:------|:----------|
|Geometry STGeomFromText (String WKT, int SRID)| Constructeur pour une instance Geometry à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text), à laquelle s’ajoutent les valeurs Z (élévation) et M (mesure) apportées par l’instance.
|Geometry STGeomFromWKB(byte[] wkb)| Constructeur pour une instance Geometry à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary).
|Désérialisation des géométries (Byte [] WKB)| Constructeur pour une instance geometry à partir d’un format de SQL Server interne pour les données spatiales.
|Analyse Geometry (chaîne WKT)| Constructeur pour une instance Geometry à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text). La valeur par défaut de l’identificateur de référence spatiale est 0.
|Point géométrique (double x, double y, entier SRID)| Constructeur pour une instance geometry qui représente une instance point à partir de ses valeurs X et Y et d’un identificateur de référence spatiale.
|String STAsText()| Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d’une instance Geometry. Ce texte ne contiendra aucune valeur Z (élévation) ou M (mesure) apportée par l'instance.
|byte[] STAsBinary()| Retourne la représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary) d’une instance Geometry. Cette valeur ne contiendra aucune valeur Z ou M apportée par l'instance.
|byte[] serialize()| Retourne les octets qui représentent un format interne SQL Server de type Geometry.
|Boolean hasM ()| Retourne si l’objet contient une valeur M (mesure).
|Boolean hasZ ()| Retourne si l’objet contient une valeur Z (élévation).
|Double getX()| Retourne la valeur de la coordonnée X.
|Double getY()| Retourne la valeur de la coordonnée Y.
|Double getM()| Retourne la valeur M (mesure) de l’objet.
|Double getZ()| Retourne la valeur Z (élévation) de l’objet.
|int getSrid()| Retourne la valeur de l’identificateur de référence spatiale (SRID).
|valeurs booléennes isNull ()| Retourne si l’objet Geometry a la valeur null.
|int STNumPoints()| Retourne le nombre de points dans l’objet Geometry.
|Chaîne STGeometryType ()| Retourne le nom de type OGC (Open Geospatial Consortium) représenté par une instance géométrique.
|Chaîne asTextZM ()| Retourne la représentation de texte bien connu (WKT) de l’objet Geometry.
|Chaîne toString ()| Retourne la représentation de chaîne de l’objet Geometry.

### <a name="geography"></a>Géographie

|Méthode|Description|
|:------|:----------|
|Geography STGeomFromText (String WKT, int SRID)| Constructeur pour une instance Geography à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text), à laquelle s’ajoutent les valeurs Z (élévation) et M (mesure) apportées par l’instance.
|Geography STGeomFromWKB(byte[] wkb)| Constructeur pour une instance Geography à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary).
|Geography deserialize(byte[] wkb)| Constructeur pour une instance geography à partir d’un format de SQL Server interne pour les données spatiales.
|Analyse Geography (chaîne WKT)| Constructeur pour une instance Geography à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text). La valeur par défaut de l’identificateur de référence spatiale est 0.
|Point géographique (double lon, double lat, int SRID)| Constructeur pour une instance Geography qui représente une instance Point à partir de sa longitude et de sa latitude, et d’un ID de référence spatiale.
|String STAsText()| Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d’une instance Geography. Ce texte ne contiendra aucune valeur Z (élévation) ou M (mesure) apportée par l'instance.
|byte[] STAsBinary())| Retourne la représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary) d’une instance Geography. Cette valeur ne contiendra aucune valeur Z ou M apportée par l'instance.
|byte[] serialize()| Retourne les octets qui représentent un format interne SQL Server de type Geography.
|Boolean hasM ()| Retourne si l’objet contient une valeur M (mesure).
|Boolean hasZ ()| Retourne si l’objet contient une valeur Z (élévation).
|Double getLatitude()| Retourne la valeur de latitude.
|Double getLongitude()| Retourne la valeur de longitude.
|Double getM()| Retourne la valeur M (mesure) de l’objet.
|Double getZ()| Retourne la valeur Z (élévation) de l’objet.
|int getSrid()| Retourne la valeur de l’identificateur de référence spatiale (SRID).
|valeurs booléennes isNull ()| Retourne si l’objet Geography a la valeur null.
|int STNumPoints()| Retourne le nombre de points dans l’objet geography.
|Chaîne STGeographyType ()| Retourne le nom de type OGC (Open Geospatial Consortium) représenté par une instance géographique.
|Chaîne asTextZM ()| Retourne la représentation de texte connu (WKT) de l’objet geography.
|Chaîne toString ()| Retourne la représentation de chaîne de l’objet Geography.

## <a name="limitations-of-spatial-datatypes"></a>Limitations des types de données spatiaux

1. Les sous-types de données spatiaux **CircularString**, **CompoundCurve**, **CurvePolygon**et **FullGlobe** ne sont pris en charge qu’à partir de SQL Server 2012 et versions ultérieures.

2. Always Encrypted ne peut pas être utilisé avec des types de données spatiaux.

3. Les procédures stockées, les TVP et les opérations BulkCopy ne sont actuellement pas pris en charge avec les types de données spatiaux.

## <a name="see-also"></a>Voir aussi

[Exemple de types de données spatiales (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)
