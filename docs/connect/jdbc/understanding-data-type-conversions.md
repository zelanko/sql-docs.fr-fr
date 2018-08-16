---
title: Conversions de types de données de présentation | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 98fa7488-aac3-45b4-8aa4-83ed6ab638b4
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0164fdcfebdf0fb92aac1f37820495ad8e591a41
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662201"
---
# <a name="understanding-data-type-conversions"></a>Conversions de types de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour faciliter la conversion des types de données du langage de programmation Java en types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] assure les conversions des types de données requises par la spécification JDBC. Pour une flexibilité accrue, tous les types sont convertibles vers et depuis **objet**, **chaîne**, et **byte []** types de données.

## <a name="getter-method-conversions"></a>Conversions de méthode d'accesseur Get

Le tableau suivant, basé sur les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], présente le mappage des conversions du pilote JDBC pour les méthodes get\<Type>() de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), ainsi que les conversions prises en charge pour les méthodes get\<Type> de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md).

![JDBCGetterConversions](../../connect/jdbc/media/jdbcgetterconversions.gif "JDBCGetterConversions")

Trois catégories de conversions sont prises en charge par les méthodes d'accesseur Get du pilote JDBC :

- **Sans perte (x)** : conversions pour le cas où le type getter est inférieur ou égal au type serveur sous-jacent. Par exemple, lors de l’appel de getBigDecimal sur une colonne décimale de serveur sous-jacente, aucune conversion n’est nécessaire.

- **Convertie (y)** : conversions de types serveur numériques en types du langage Java, où la conversion est standard et suit les règles de conversion du langage Java. Pour ces conversions, la précision est toujours tronquée (jamais arrondie) et les dépassements sont gérés comme un opérateur modulo du type de destination, qui est plus petit. Par exemple, l’appel getInt sur sous-jacent **décimal** colonne qui contient « 1,9999 » retournera « 1 », ou si sous-jacent **décimal** valeur est « 3000000000 », le **int** valeur engendre un dépassement à « -1294967296 ».

- **Dépendante des données (z)** : les conversions de types de caractère sous-jacents en types numériques nécessitent que les types caractère contiennent des valeurs pouvant être converties dans ce type. Aucune autre conversion n'a lieu. Si la valeur est trop élevée pour le type getter, elle n’est pas valide. Par exemple, si getInt est appelée sur une colonne varchar(50) contenant « 53 », la valeur est retournée en tant que **int** ; en revanche, si la valeur sous-jacente est « xyz » ou « 3000000000 », une erreur est générée.

Si getString est appelée sur un **binaire**, **varbinary**, **varbinary (max)**, ou **image** de type de données de colonne, la valeur est retournée comme un valeur de chaîne hexadécimale.

## <a name="updater-method-conversions"></a>Conversions de méthodes Updater

Pour les données typées Java passées aux méthodes \<Type>() de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), les conversions suivantes s’appliquent.

![JDBCUpdaterConversions](../../connect/jdbc/media/jdbc_jdbcupdatterconversions.gif "JDBCUpdaterConversions")

Trois catégories de conversions sont prises en charge par les méthodes updater du pilote JDBC :

- **Sans perte (x)** : conversions pour le cas où le type updater est inférieur ou égal au type serveur sous-jacent. Par exemple, lors de l'appel de updateBigDecimal sur une colonne décimale de serveur sous-jacente, aucune conversion n'est nécessaire.

- **Convertie (y)** : conversions de types serveur numériques en types du langage Java, où la conversion est standard et suit les règles de conversion du langage Java. Pour ces conversions, la précision est toujours tronquée (jamais arrondie) et le dépassement de capacité est géré en tant que modulo du type de destination (type le plus petit). Par exemple, l’appel updateDecimal sur sous-jacent **int** colonne qui contient « 1,9999 » retournera « 1 », ou si sous-jacent **décimal** valeur est « 3000000000 », puis le **int**valeur engendre un dépassement à « -1294967296 ».

- **Dépendante des données (z)** : les conversions de types de données sources sous-jacents en types de données de destination nécessitent que les valeurs contenues puissent être converties dans les types de destination. Aucune autre conversion n'a lieu. Si la valeur est trop élevée pour le type getter, elle n’est pas valide. Par exemple, si updateString est appelé sur une colonne int qui contient « 53 », la mise à jour réussit ; toutefois, si la valeur String sous-jacente est « foo » ou « 3000000000 », une erreur est générée.

Lorsque updateString est appelé sur un **binaire**, **varbinary**, **varbinary (max)**, ou **image** de type de données de colonne, il gère la valeur de chaîne en tant que valeur de chaîne hexadécimale.

Quand le type de données de colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] est **XML**, la valeur des données doit être du **XML**valide. Lors de l’appel updateBytes, updateBinaryStream ou updateBlob méthodes, la valeur de données doit être la représentation sous forme de chaîne hexadécimale des caractères XML. Exemple :

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

Notez qu'une marque d'ordre d'octet (BOM, Byte-Order Mark) est obligatoire si les caractères XML correspondent à des encodages de caractères spécifiques.

## <a name="setter-method-conversions"></a>Conversions de méthodes setter

Pour les données typées Java passées aux méthodes set\<Type>() de la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et de la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), les conversions suivantes s’appliquent.

![JDBCSetterConversions](../../connect/jdbc/media/jdbc_jdbcsetterconversions_v2.gif "JDBCSetterConversions")

Le serveur tente toutes les conversions et retourne des erreurs en cas d'échec.

Dans le cas de la **chaîne** type de données, si la valeur dépasse la longueur de **VARCHAR**, il est mappé à **LONGVARCHAR**. De même, **NVARCHAR** est mappé à **LONGNVARCHAR** si la valeur dépasse la longueur prise en charge de **NVARCHAR**. Il en va de même pour **byte[]**. Valeurs de plus de **VARBINARY** deviennent **LONGVARBINARY**.

Deux catégories de conversions sont prises en charge par les méthodes setter du pilote JDBC :

- **Sans perte (x)** : conversions pour le cas numériques où le type setter est inférieur ou égal au type serveur sous-jacent. Par exemple, lors de l’appel de setBigDecimal sur une colonne **decimal** de serveur sous-jacente, aucune conversion n’est nécessaire. Pour les conversions de numérique à caractère, le type de données **numeric** Java est converti en **String**. Par exemple, l’appel de setDouble avec une valeur « 53 » sur une colonne varchar(50) produit une valeur caractère « 53 » dans cette colonne de destination.

- **Converti (y)**: Conversions à partir de Java **numérique** type serveur sous-jacent **numérique** type qui est plus petite. Ces conversions sont standard et suivent les conventions de conversion [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. La précision est toujours tronquée (jamais arrondie) et tout dépassement de capacité génère une erreur de conversion non prise en charge. Par exemple, l’utilisation de updateDecimal avec la valeur « 1,9999 » sur une colonne d’entiers sous-jacente produit « 1 » dans la colonne de destination ; en revanche, si la valeur « 3000000000 » est passée, le pilote génère une erreur.

- **Dépendant des données (z)**: Conversions à partir de Java **chaîne** type sous-jacent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] type de données varie selon les conditions suivantes : le pilote envoie le **chaîne** valeur à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] effectue des conversions, si nécessaire. Si sendStringParametersAsUnicode est définie sur true et que le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sous-jacent est **image**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] n’autorise pas la conversion de **nvarchar** en **image** et lève une exception SQLServerException. Si sendStringParametersAsUnicode est défini sur false et que le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sous-jacent est **image**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] permet la conversion de **varchar** en **image** et aucune exception n’est levée.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] effectue les conversions et retourne les erreurs au pilote JDBC en cas de problème.

Quand le type de données de colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] est **XML**, la valeur des données doit être du **XML**valide. Lors de l’appel updateBytes, updateBinaryStream ou updateBlob méthodes, la valeur de données doit être la représentation sous forme de chaîne hexadécimale des caractères XML. Exemple :

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

Notez qu'une marque d'ordre d'octet (BOM, Byte-Order Mark) est obligatoire si les caractères XML correspondent à des encodages de caractères spécifiques.

## <a name="conversions-on-setobject"></a>Conversions sur setObject

> [!NOTE]  
> Pilotes Microsoft JDBC 4.2 (et versions ultérieures) pour SQL Server prend en charge JDBC 4.1 et 4.2. Pour plus d’informations sur les mappages de type de données et les conversions 4.1 et 4.2, consultez [conformité JDBC 4.1 pour le pilote JDBC](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) et [JDBC 4.2 conformité pour le pilote JDBC](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md), outre les informations ci-dessous.

Pour les données typées Java passées aux méthodes setObject(\<Type>) de la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), les conversions suivantes s’appliquent.

![JDBCSetObjectConversions](../../connect/jdbc/media/jdbc_jdbcsetobjectconversions.gif "JDBCSetObjectConversions")

La méthode setObject sans type cible spécifié utilise le mappage par défaut. Dans le cas de la **chaîne** type de données, si la valeur dépasse la longueur de **VARCHAR**, il est mappé à **LONGVARCHAR**. De même, **NVARCHAR** est mappé à **LONGNVARCHAR** si la valeur dépasse la longueur prise en charge de **NVARCHAR**. Il en va de même pour **byte[]**. Valeurs de plus de **VARBINARY** deviennent **LONGVARBINARY**.

Trois catégories de conversions sont prises en charge par les méthodes setObject du pilote JDBC :

- **Sans perte (x)** : conversions pour le cas numériques où le type setter est inférieur ou égal au type serveur sous-jacent. Par exemple, lors de l’appel de setBigDecimal sur une colonne **decimal** de serveur sous-jacente, aucune conversion n’est nécessaire. Pour les conversions de numérique à caractère, le type de données **numeric** Java est converti en **String**. Par exemple, l’appel de setDouble avec une valeur « 53 » sur une colonne varchar(50) produit une valeur caractère « 53 » dans cette colonne de destination.

- **Converti (y)**: Conversions à partir de Java **numérique** type serveur sous-jacent **numérique** type qui est plus petite. Ces conversions sont standard et suivent les conventions de conversion [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. La précision est toujours tronquée (jamais arrondie) et les dépassements génèrent une erreur de conversion non prise en charge. Par exemple, l’utilisation de updateDecimal avec la valeur « 1,9999 » sur une colonne d’entiers sous-jacente produit « 1 » dans la colonne de destination ; en revanche, si la valeur « 3000000000 » est passée, le pilote génère une erreur.

- **Dépendant des données (z)**: Conversions à partir de Java **chaîne** type sous-jacent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] type de données varie selon les conditions suivantes : le pilote envoie le **chaîne** valeur à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] effectue des conversions, si nécessaire. Si la propriété de connexion sendStringParametersAsUnicode est définie sur true et que le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sous-jacent est **image**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] n’autorise pas la conversion de **nvarchar** en **image** et lève une exception SQLServerException. Si sendStringParametersAsUnicode est défini sur false et que le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sous-jacent est **image**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] permet la conversion de **varchar** en **image** et aucune exception n’est levée.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] effectue les conversions de définitions en masse et retourne les erreurs au pilote JDBC en cas de problème. Conversions côté client constituent l’exception et sont effectuées uniquement dans le cas de **date**, **temps**, **timestamp**, **booléenne**et  **Chaîne** valeurs.

Quand le type de données de colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] est **XML**, la valeur des données doit être du **XML**valide. Lors de l'appel des méthodes setObject(byte[], SQLXML), setObject(inputStream, SQLXML) ou setObject(Blob, SQLXML), la valeur de données doit être la représentation sous forme de chaîne hexadécimale des caractères XML. Exemple :

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

Notez qu'une marque d'ordre d'octet (BOM, Byte-Order Mark) est obligatoire si les caractères XML correspondent à des encodages de caractères spécifiques.

## <a name="see-also"></a> Voir aussi

[Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
