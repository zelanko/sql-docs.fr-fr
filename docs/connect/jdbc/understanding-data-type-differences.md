---
title: Comprendre les différences entre les types de données | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 906a4abf0768fcad2e5ac31a0ee93345dcc8b30c
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027382"
---
# <a name="understanding-data-type-differences"></a>Présentation des différences entre les types de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Il existe de nombreuses différences entre les types de données du langage de programmation Java et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] vous aide à maîtriser les différences entre ces différents types de conversions.  

## <a name="character-types"></a>Types de caractères

Les types de données de chaîne de caractères JDBC sont **char**, **varchar**et **LONGVARCHAR**. Le pilote JDBC prend en charge l'API JDBC 4.0. Dans le JDBC 4,0, les types de données de chaîne de caractères JDBC peuvent également être **nchar**, **nvarchar**et **LONGNVARCHAR**. Ces nouveaux types de chaînes de caractères conservent les types de caractères natifs Java au format Unicode et rendent inutiles les conversions ANSI vers Unicode ou Unicode vers ANSI.  
  
| Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Longueur fixe    | Les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données **char** et **nchar** sont mappés directement aux types **char** et **nchar** JDBC. Il s’agit de types de longueur fixe avec un remplissage fourni par le serveur au cas où la colonne a `SET ANSI_PADDING ON`. Le remplissage est toujours activé pour **nchar** ; toutefois, pour **char**, si les colonnes char du serveur ne sont pas remplies, le pilote JDBC ajoute le remplissage.                                                                                                                                                                                                                                                                                                                                                                                      |
| Longueur variable | Les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types **varchar** et **nvarchar** sont mappés directement aux types JDBC **varchar** et **nvarchar** , respectivement.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Long            | Les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types **Text** et **ntext** sont respectivement mappés aux types **LONGVARCHAR** et **LONGNVARCHAR** de JDBC. Il s’agit de types dépréciés à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. vous devez donc utiliser des types de valeur élevée, **varchar (max)** ou **nvarchar (max)** , à la place.<br /><br /> L’utilisation des\<méthodes de mise à jour de type numérique > et [updateObject (int, Java. lang. Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) échoue sur les colonnes de serveur **Text** et **ntext** . Cependant, l’utilisation de la méthode [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) avec un type de conversion de caractère spécifié est prise en charge sur les colonnes de serveur **text** et **ntext**. |
  
## <a name="binary-string-types"></a>Types de chaînes binaires

Les types de chaînes binaires JDBC sont **Binary**, **varbinary**et **LONGVARBINARY**.  
  
| Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Longueur fixe    | Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type **binaire** est mappé directement au type **binaire** JDBC. Il s'agit d'un type de longueur fixe avec une marge fournie par le serveur au cas où la colonne a SET ANSI_PADDING ON. Si les colonnes char du serveur ne disposent pas de marge, le pilote JDBC ajoute la marge.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type d' **horodatage** est un type **binaire** JDBC dont la longueur fixe est de 8 octets. |
| Longueur variable | Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type **varbinary** est mappé au type **varbinary** JDBC.<br /><br /> Le type **UDT** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est mappé à JDBC en tant que type **varbinary** .                                                                                                                                                                                                                                 |
| Long            | Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type d' **image** est mappé au type JDBC **LONGVARBINARY** . Ce type est déprécié à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ; par conséquent, vous devez utiliser un type de grande valeur, **varbinary(max)** , à la place.                                                                                                                                                                                           |
  
## <a name="exact-numeric-types"></a>Types numériques exacts

Les types numériques exacts JDBC sont mappés directement aux types SQL Server correspondants.  
  
| Type     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BIT      | Le type JDBC **BIT** représente un bit unique qui peut être 0 ou 1. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de **bit** .                                                                                                                                                                                                                                                                                                                                       |
| TINYINT  | Le type JDBC **TINYINT** représente un octet unique. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type **tinyint** .                                                                                                                                                                                                                                                                                                                                                 |
| SMALLINT | Le type JDBC **SMALLINT** représente un entier signé de 16 bits. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type **smallint** .                                                                                                                                                                                                                                                                                                                                     |
| INTEGER  | Le type JDBC **INTEGER** représente un entier signé de 32 bits. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type **int** .                                                                                                                                                                                                                                                                                                                                           |
| bigint   | Le type JDBC **BIGINT** représente un entier signé de 64 bits. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type **bigint** .                                                                                                                                                                                                                                                                                                                                         |
| NUMERIC  | Le type JDBC **NUMERIC** représente une valeur décimale à précision fixe qui conserve des valeurs de précision identique. Le type **numérique** est mappé au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type **numérique** .                                                                                                                                                                                                                                                                   |
| DECIMAL  | Le type JDBC **DECIMAL** représente une valeur décimale à précision fixe qui conserve au minimum des valeurs de la précision spécifiée. Le type **décimal** est mappé au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type **décimal** .<br /><br /> Le type JDBC **DECIMAL** est également mappé aux types [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **money** et **smallmoney**, qui sont des types décimaux à précision fixe spécifiques stockés respectivement sur 8 et 4 octets. |
  
## <a name="approximate-numeric-types"></a>Types numériques approximatifs

Les types numériques approximatifs JDBC sont **Real**, **double**et **float**.  
  
| Type   | Description                                                                                                                                                                                                                                                                                                   |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| real   | Le type JDBC **REAL** a sept chiffres de précision (précision unique) et correspond directement au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **real**.                                                                                                                                     |
| DOUBLE | Le type JDBC **DOUBLE** a 15 chiffres de précision (précision double) et est mappé au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float**. Le type **float** JDBC est un synonyme de **double**. Étant donné qu’il peut y avoir confusion entre **float** et **double**, **double** est préférable. |
  
## <a name="datetime-types"></a>Types de date/d'heure

Le type d' **horodatage** JDBC est mappé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux types **DateTime** et **smalldatetime** . Le type **datetime** est stocké dans deux entiers de 4 octets. Le type **smalldatetime** conserve les mêmes informations (date et heure), mais avec une précision inférieure, dans deux petits entiers de 2 octets.  
  
> [!NOTE]  
> Le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** est un type de chaîne binaire de longueur fixe. Elle ne correspond à aucun des types d’heure JDBC: **Date**, **Time**ou **timestamp**.  
  
## <a name="custom-type-mapping"></a>Mappage de types personnalisés

La fonction de mappage de type personnalisé de JDBC qui utilise les interfaces SQLData pour les types avancés JDBC (UDT, Struct, et ainsi de suite). n'est pas implémentée dans le pilote JDBC.  
  
## <a name="see-also"></a>Voir aussi

[Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
