---
title: Présentation des différences entre les types de données
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5395b915d2f261813495d364730d0442a8139334
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992941"
---
# <a name="understanding-data-type-differences"></a>Différences entre les types de données
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il existe de nombreuses différences entre les types de données du langage de programmation Java et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] vous aide à maîtriser les différences entre ces différents types de conversions.  
  
## <a name="character-types"></a>Types de caractères  
 Les types de données de chaîne de caractères JDBC sont **CHAR**, **VARCHAR**, et **LONGVARCHAR**. Le pilote JDBC prend en charge l'API JDBC 4.0. Dans JDBC 4.0, les types de données de chaîne de caractères JDBC peuvent également être **NCHAR**, **NVARCHAR**, et **LONGNVARCHAR**. Ces nouveaux types de chaînes de caractères conservent les types de caractères natifs Java au format Unicode et rendent inutiles les conversions ANSI vers Unicode ou Unicode vers ANSI.  
  
|Type|Description|  
|----------|-----------------|  
|Longueur fixe|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **char** et **nchar** types de données mappent directement aux types JDBC **CHAR** et **NCHAR** types. Il s'agit de types de longueur fixe avec un remplissage fourni par le serveur au cas où la colonne a SET ANSI_PADDING ON. Le remplissage est toujours activé pour **nchar** ; toutefois, pour **char**, si les colonnes char du serveur ne sont pas remplies, le pilote JDBC ajoute le remplissage.|  
|Longueur variable|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **varchar** et **nvarchar** types mappent directement aux types JDBC **VARCHAR** et **NVARCHAR** types, respectivement.|  
|Long|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **texte** et **ntext** types mappent aux types JDBC **LONGVARCHAR** et **LONGNVARCHAR** tapez, respectivement. Ces types sont déconseillés à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] ; par conséquent, vous devez utiliser des types de grande valeur, **ou** à la place.<br /><br /> À l’aide de la mise à jour\<Type numérique > et [updateObject (int, java.lang.Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) méthodes échoue sur **texte** et **ntext** colonnes du serveur. Cependant, l’utilisation de la méthode [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) avec un type de conversion de caractère spécifié est prise en charge sur les colonnes de serveur **text** et **ntext**.|  
  
## <a name="binary-string-types"></a>Types de chaînes binaires  
 Les types de chaînes binaires JDBC sont **binaire**, **VARBINARY**, et **LONGVARBINARY**.  
  
|Type|Description|  
|----------|-----------------|  
|Longueur fixe|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **binaire** tapez est directement mappée à JDBC **binaire** type. Il s'agit d'un type de longueur fixe avec une marge fournie par le serveur au cas où la colonne a SET ANSI_PADDING ON. Si les colonnes char du serveur ne disposent pas de marge, le pilote JDBC ajoute la marge.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **timestamp** type est un JDBC **binaire** type avec une longueur fixe de 8 octets.|  
|Longueur variable|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **varbinary** type est mappé à JDBC **VARBINARY** type.<br /><br /> Le **udt** tapez [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] mappe à JDBC comme un **VARBINARY** type.|  
|Long|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **image** type est mappé à JDBC **LONGVARBINARY** type. Ce type est déprécié à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] ; par conséquent, vous devez utiliser un type de grande valeur, **varbinary(max)**, à la place.|  
  
## <a name="exact-numeric-types"></a>Types numériques exacts  
 Les types numériques exacts JDBC sont mappés directement aux types SQL Server correspondants.  
  
|Type|Description|  
|----------|-----------------|  
|BIT|Le type JDBC **BIT** représente un bit unique qui peut être 0 ou 1. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bits** type.|  
|TINYINT|Le type JDBC **TINYINT** représente un octet unique. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **tinyint** type.|  
|SMALLINT|Le type JDBC **SMALLINT** représente un entier signé de 16 bits. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **smallint** type.|  
|INTEGER|Le type JDBC **INTEGER** représente un entier signé de 32 bits. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **int** type.|  
|bigint|Le type JDBC **BIGINT** représente un entier signé de 64 bits. Correspond à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bigint** type.|  
|NUMERIC|Le type JDBC **NUMERIC** représente une valeur décimale à précision fixe qui conserve des valeurs de précision identique. Le **numérique** type est mappé sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **numérique** type.|  
|DECIMAL|Le type JDBC **DECIMAL** représente une valeur décimale à précision fixe qui conserve au minimum des valeurs de la précision spécifiée. Le **décimal** type est mappé sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **décimal** type.<br /><br /> Le type JDBC **DECIMAL** est également mappé aux types [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**money** et **smallmoney**, qui sont des types décimaux à précision fixe spécifiques stockés respectivement dans 8 et 4 octets.|  
  
## <a name="approximate-numeric-types"></a>Types numériques approximatifs  
 Les types numériques approximatifs JDBC sont **réel**, **DOUBLE**, et **FLOAT**.  
  
|Type|Description|  
|----------|-----------------|  
|real|Le type JDBC **REAL** a sept chiffres de précision (précision unique) et correspond directement au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **real**.|  
|DOUBLE|Le type JDBC **DOUBLE** a 15 chiffres de précision (précision double) et est mappé au type [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**float**. JDBC **FLOAT** type est un synonyme de **DOUBLE**. Car il peut y avoir confusion entre **FLOAT** et **DOUBLE**, **DOUBLE** est préféré.|  
  
## <a name="datetime-types"></a>Types de date/d'heure  
 JDBC **TIMESTAMP** type est mappé sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime** et **smalldatetime** types. Le type **datetime** est stocké dans deux entiers de 4 octets. Le type **smalldatetime** conserve les mêmes informations (date et heure), mais avec une précision inférieure, dans deux petits entiers de 2 octets.  
  
> [!NOTE]  
>  Le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**timestamp** est un type de chaîne binaire de longueur fixe. Il ne correspond à aucun des types d’heure JDBC : **DATE**, **temps**, ou **TIMESTAMP**.  
  
## <a name="custom-type-mapping"></a>Mappage de type personnalisé  
 La fonction de mappage de type personnalisé de JDBC qui utilise les interfaces SQLData pour les types avancés JDBC (UDT, Struct, et ainsi de suite). n'est pas implémentée dans le pilote JDBC.  
  
## <a name="see-also"></a> Voir aussi  
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
