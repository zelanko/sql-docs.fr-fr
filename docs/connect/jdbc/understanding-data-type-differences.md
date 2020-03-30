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
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027382"
---
# <a name="understanding-data-type-differences"></a>Présentation des différences entre les types de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Il existe de nombreuses différences entre les types de données du langage de programmation Java et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] vous aide à maîtriser les différences entre ces différents types de conversions.  

## <a name="character-types"></a>Types de caractères

Les types de données de chaîne de caractères JDBC sont **CHAR**, **VARCHAR** et **LONGVARCHAR**. Le pilote JDBC prend en charge l'API JDBC 4.0. Dans JDBC 4.0, les types de données de chaîne de caractères JDBC peuvent également être **NCHAR**, **NVARCHAR** et **LONGNVARCHAR**. Ces nouveaux types de chaînes de caractères conservent les types de caractères natifs Java au format Unicode et rendent inutiles les conversions ANSI vers Unicode ou Unicode vers ANSI.  
  
| Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Longueur fixe    | Les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char** et **nchar** correspondent directement aux types JDBC **CHAR** et **NCHAR**. Il s’agit de types de longueur fixe avec un remplissage fourni par le serveur au cas où la colonne a `SET ANSI_PADDING ON`. Le remplissage est toujours activé pour **nchar** ; toutefois, pour **char**, si les colonnes char du serveur ne sont pas remplies, le pilote JDBC ajoute le remplissage.                                                                                                                                                                                                                                                                                                                                                                                      |
| Longueur variable | Les types [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **varchar** et **nvarchar** correspondent directement et respectivement aux types JDBC **VARCHAR** et **NVARCHAR**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Long            | Les types [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **text** et **ntext** correspondent respectivement aux types JDBC **LONGVARCHAR** et **LONGNVARCHAR**. Ces types sont déconseillés à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ; utilisez à la place des types de grande valeur, **varchar(max)** ou **nvarchar(max)** .<br /><br /> Les méthodes update\<Type numérique> et [updateObject (int, java.lang.Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) échoueront sur des colonnes serveur **text** et **ntext**. Cependant, l’utilisation de la méthode [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) avec un type de conversion de caractère spécifié est prise en charge sur les colonnes de serveur **text** et **ntext**. |
  
## <a name="binary-string-types"></a>Types de chaînes binaires

Les types de chaînes binaires JDBC sont **BINARY**, **VARBINARY** et **LONGVARBINARY**.  
  
| Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Longueur fixe    | Le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **binary** correspond directement au type JDBC **BINARY**. Il s'agit d'un type de longueur fixe avec une marge fournie par le serveur au cas où la colonne a SET ANSI_PADDING ON. Si les colonnes char du serveur ne disposent pas de marge, le pilote JDBC ajoute la marge.<br /><br /> Le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** est un type JDBC **BINARY** de longueur fixe de 8 octets. |
| Longueur variable | Le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **varbinary** correspond au type JDBC **VARBINARY**.<br /><br /> Le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **udt** correspond au type JDBC **VARBINARY**.                                                                                                                                                                                                                                 |
| Long            | Le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **image** correspond au type JDBC **LONGVARBINARY**. Ce type est déprécié à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ; par conséquent, vous devez utiliser un type de grande valeur, **varbinary(max)** , à la place.                                                                                                                                                                                           |
  
## <a name="exact-numeric-types"></a>Types numériques exacts

Les types numériques exacts JDBC sont mappés directement aux types SQL Server correspondants.  
  
| Type     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BIT      | Le type JDBC **BIT** représente un bit unique qui peut être 0 ou 1. Il correspond au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit**.                                                                                                                                                                                                                                                                                                                                       |
| TINYINT  | Le type JDBC **TINYINT** représente un octet unique. Il correspond au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **tinyint**.                                                                                                                                                                                                                                                                                                                                                 |
| SMALLINT | Le type JDBC **SMALLINT** représente un entier signé de 16 bits. Il correspond au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **smallint**.                                                                                                                                                                                                                                                                                                                                     |
| INTEGER  | Le type JDBC **INTEGER** représente un entier signé de 32 bits. Il correspond au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **int**.                                                                                                                                                                                                                                                                                                                                           |
| bigint   | Le type JDBC **BIGINT** représente un entier signé de 64 bits. Il correspond au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bigint**.                                                                                                                                                                                                                                                                                                                                         |
| NUMERIC  | Le type JDBC **NUMERIC** représente une valeur décimale à précision fixe qui conserve des valeurs de précision identique. Le type **NUMERIC** correspond au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **numeric**.                                                                                                                                                                                                                                                                   |
| DECIMAL  | Le type JDBC **DECIMAL** représente une valeur décimale à précision fixe qui conserve au minimum des valeurs de la précision spécifiée. Le type **DECIMAL** correspond au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **decimal**.<br /><br /> Le type JDBC **DECIMAL** correspond également aux types [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **money** et **smallmoney**, qui sont des types décimaux à précision fixe spécifiques stockés respectivement sur 8 et 4 octets. |
  
## <a name="approximate-numeric-types"></a>Types numériques approximatifs

Les types numériques approximatifs JDBC sont **REAL**, **DOUBLE** et **FLOAT**.  
  
| Type   | Description                                                                                                                                                                                                                                                                                                   |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| real   | Le type JDBC **REAL**, d’une précision à 7 chiffres (simple précision), correspond directement au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **real**.                                                                                                                                     |
| DOUBLE | Le type JDBC **DOUBLE**, d’une précision à 15 chiffres (double précision), correspond au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float**. Le type JDBC **FLOAT** est un synonyme de **DOUBLE**. Compte tenu de la confusion possible entre **FLOAT** et **DOUBLE**, **DOUBLE** est préférable. |
  
## <a name="datetime-types"></a>Types de date/d'heure

Le type JDBC **TIMESTAMP** correspond aux types [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** et **smalldatetime**. Le type **datetime** est stocké dans deux entiers de 4 octets. Le type **smalldatetime** conserve les mêmes informations (date et heure), mais avec une précision inférieure, dans deux petits entiers de 2 octets.  
  
> [!NOTE]  
> Le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** est un type de chaîne binaire de longueur fixe. Il ne correspond à aucun type de temps JDBC : **DATE**, **TIME** et **TIMESTAMP**.  
  
## <a name="custom-type-mapping"></a>Mappage de types personnalisés

La fonction de mappage de type personnalisé de JDBC qui utilise les interfaces SQLData pour les types avancés JDBC (UDT, Struct, et ainsi de suite). n'est pas implémentée dans le pilote JDBC.  
  
## <a name="see-also"></a>Voir aussi

[Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
