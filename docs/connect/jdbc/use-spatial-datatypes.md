---
description: Utilisation des types de données spatiales
title: Utilisation des types de données spatiales | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02b545ec1d33d17674266d58a2a120f07af423ad
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727526"
---
# <a name="using-spatial-datatypes"></a>Utilisation des types de données spatiales

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les types de données spatiales (Geometry et Geography) sont pris en charge à partir de la préversion du pilote JDBC 6.5.0. Les types de données spatiales ne sont actuellement pas pris en charge avec les procédures stockées, les paramètres table (TVP), BulkCopy et Always Encrypted. Cette page présente divers cas d’usage des types de données Geometry et Geography avec le pilote JDBC. Pour une vue d’ensemble des types de données spatiales, consultez [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md).

## <a name="creating-a-geometry--geography-object"></a>Création d’un objet Geometry/Geography

Il existe deux façons de créer un objet Geometry/Geography : convertir un texte bien connu (WKT) ou un format SQL Server interne (CLR).

### <a name="creating-from-wkt"></a>Créer à partir d’un WKT

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

Cela permet de créer un objet Geometry LINESTRING avec l’identificateur de système de référence spatiale (SRID) 0 et un objet Geography avec le SRID 4326.

### <a name="creating-from-clr"></a>Créer à partir d’un CLR

```java
byte[] geomCLR = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogCLR = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomCLR);
Geography geogWKT = Geography.deserialize(geogCLR);
```

Cela créera des objets Geometry et Geography équivalents à ceux créés à partir du WKT précédemment.

## <a name="working-with-a-geometry--geography-object"></a>Utilisation d’un objet Geometry/Geography

En supposant que l’utilisateur dispose d’une table sur SQL Server comme ci-dessous :

```sql
CREATE TABLE sampleTable (c1 geometry)  
```

Voici un exemple de script pour insérer une valeur Geometry :

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) connection.prepareStatement("insert into sampleTable values (?)");
pstmt.setGeometry(1, geomWKT);  
pstmt.execute();
```

La même opération peut être effectuée pour la contrepartie Geography, à l’aide d’une colonne Geography et de la méthode **setGeography()**.

Pour lire une colonne Geometry/Geography :

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

La même opération peut être effectuée pour la contrepartie Geography, à l’aide d’une colonne Geography et de la méthode **getGeography()**.

## <a name="newly-introduced-apis"></a>API récemment introduites

Il s’agit des nouvelles API publiques introduites dans cet ajout, dans les classes **SQLServerPreparedStatement**, **SQLServerResultSet**, **Geometry** et **Geography**.

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|Méthode|Description|
|:------|:----------|
|void setGeometry(int n, Geometry x)| Définit le paramètre désigné pour l’objet de classe microsoft.Sql.Geometry donné.
|void setGeography(int n, Geography x)| Définit le paramètre désigné pour l’objet de classe microsoft.Sql.Geography donné.

### <a name="sqlserverresultset"></a>SQLServerResultSet

|Méthode|Description|
|:------|:----------|
|Geometry getGeometry(int colunIndex)| Renvoie la valeur de la colonne désignée dans la ligne actuelle de cet objet ResultSet en tant qu’objet com.microsoft.sqlserver.jdbc.Geometry dans le langage de programmation Java.
|Geometry getGeometry(String columnName)| Renvoie la valeur de la colonne désignée dans la ligne actuelle de cet objet ResultSet en tant qu’objet com.microsoft.sqlserver.jdbc.Geometry dans le langage de programmation Java.
|Geography getGeography(int colunIndex)| Renvoie la valeur de la colonne désignée dans la ligne actuelle de cet objet ResultSet en tant qu’objet com.microsoft.sqlserver.jdbc.Geography dans le langage de programmation Java.
|Geography getGeography(String columnName)| Renvoie la valeur de la colonne désignée dans la ligne actuelle de cet objet ResultSet en tant qu’objet com.microsoft.sqlserver.jdbc.Geography dans le langage de programmation Java.

### <a name="geometry"></a>Géométrie

|Méthode|Description|
|:------|:----------|
|Geometry STGeomFromText(String wkt, int SRID)| Constructeur pour une instance Geometry à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text), à laquelle s’ajoutent les valeurs Z (élévation) et M (mesure) apportées par l’instance.
|Geometry STGeomFromWKB(byte[] wkb)| Constructeur pour une instance Geometry à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary). Remarque : Cette méthode utilise actuellement le format SQL Server interne (CLR) pour créer une instance Geometry ; c’est un problème connu du pilote et ce comportement devrait changer pour accepter des données WKB à la place. Pour les utilisateurs existants qui utilisent déjà cette méthode, envisagez de passer à deserialize(byte) à la place.
|Geometries deserialize(byte[] clr)| Constructeur pour une instance Geometry construite à partir d'un format interne SQL Server pour les données spatiales.
|Geometry parse(String wkt)| Constructeur pour une instance Geometry à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text). La valeur par défaut de l’identificateur de référence spatiale est 0.
|Geometry point(double x, double y, int SRID)| Constructeur pour une instance Geometry qui représente une instance Point à partir de ses valeurs X et Y, et d’un ID de référence spatiale.
|String STAsText()| Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d’une instance Geometry. Ce texte ne contiendra aucune valeur Z (élévation) ou M (mesure) apportée par l'instance.
|byte[] STAsBinary()| Retourne la représentation du format SQL Server interne (CLR) d’une instance Geometry. Cette valeur ne contiendra aucune valeur Z ou M apportée par l'instance.
|byte[] serialize()| Retourne les octets qui représentent un format interne SQL Server de type Geometry.
|boolean hasM()| Indique si l’objet contient une valeur M (mesure).
|boolean hasZ()| Indique si l’objet contient une valeur Z (élévation).
|Double getX()| Retourne la valeur de la coordonnée X.
|Double getY()| Retourne la valeur de la coordonnée Y.
|Double getM()| Renvoie la valeur M (mesure) de l’objet.
|Double getZ()| Renvoie la valeur Z (élévation) de l’objet.
|int getSrid()| Renvoie la valeur de l’identificateur de référence spatiale (SRID).
|boolean isNull()| Indique si l’objet Geometry a la valeur null.
|int STNumPoints()| Renvoie le nombre de points dans l’objet Geometry.
|String STGeometryType()| Retourne le nom de type OGC (Open Geospatial Consortium) représenté par une instance géométrique.
|String asTextZM()| Retourne la représentation en texte bien connu (WKT) de l’objet Geometry.
|String toString()| Retourne la représentation de chaîne de l’objet Geometry.

### <a name="geography"></a>Geography

|Méthode|Description|
|:------|:----------|
|Geography STGeomFromText(String wkt, int SRID)| Constructeur pour une instance Geography à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text), à laquelle s’ajoutent les valeurs Z (élévation) et M (mesure) apportées par l’instance.
|Geography STGeomFromWKB(byte[] wkb)| Constructeur pour une instance Geography à partir d’une représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary). Remarque : Cette méthode utilise actuellement le format SQL Server interne (CLR) pour créer une instance Geometry, mais à l’avenir, elle sera modifiée pour accepter des données WKB à la place, car l’équivalent SQL Server de cette méthode (STGeomFromWKB) utilise WKB. Pour les utilisateurs existants qui utilisent déjà cette méthode, envisagez de passer à deserialize(byte) à la place.
|Geography deserialize(byte[] clr)| Constructeur pour une instance Geography construite à partir d'un format interne SQL Server pour les données spatiales.
|Geography parse(String wkt)| Constructeur pour une instance Geography à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text). La valeur par défaut de l’identificateur de référence spatiale est 0.
|Geography point(double lon, double lat, int SRID)| Constructeur pour une instance Geography qui représente une instance Point à partir de sa longitude et de sa latitude, et d’un ID de référence spatiale.
|String STAsText()| Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d’une instance Geography. Ce texte ne contiendra aucune valeur Z (élévation) ou M (mesure) apportée par l'instance.
|byte[] STAsBinary())| Retourne la représentation du format SQL Server interne (CLR) d’une instance Geography. Cette valeur ne contiendra aucune valeur Z ou M apportée par l'instance.
|byte[] serialize()| Retourne les octets qui représentent un format interne SQL Server de type Geography.
|boolean hasM()| Indique si l’objet contient une valeur M (mesure).
|boolean hasZ()| Indique si l’objet contient une valeur Z (élévation).
|Double getLatitude()| Retourne la valeur de latitude.
|Double getLongitude()| Retourne la valeur de longitude.
|Double getM()| Renvoie la valeur M (mesure) de l’objet.
|Double getZ()| Renvoie la valeur Z (élévation) de l’objet.
|int getSrid()| Renvoie la valeur de l’identificateur de référence spatiale (SRID).
|boolean isNull()| Indique si l’objet Geography a la valeur null.
|int STNumPoints()| Renvoie le nombre de points dans l’objet Geography.
|String STGeographyType()| Retourne le nom de type OGC (Open Geospatial Consortium) représenté par une instance géographique.
|String asTextZM()| Retourne la représentation en texte bien connu (WKT) de l’objet Geography.
|String toString()| Retourne la représentation de chaîne de l’objet Geography.

## <a name="limitations-of-spatial-datatypes"></a>Limitations des types de données spatiales

1. Les sous-types de données spatiales **CircularString**, **CompoundCurve**, **CurvePolygon** et **FullGlobe** ne sont pris en charge qu’à partir de SQL Server 2012 et versions ultérieures.

2. Always Encrypted ne peut pas être utilisé avec des types de données spatiales.

3. Les procédures stockées, les opérations BulkCopy et les TVP ne sont actuellement pas pris en charge avec les types de données spatiales.

## <a name="see-also"></a>Voir aussi

[Exemple de types de données spatiales (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)