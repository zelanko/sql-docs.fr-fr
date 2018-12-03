---
title: Fonctionnalités internationales du pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bbb74a1d-9278-401f-9530-7b5f45aa79de
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45ad47f53b36a54843aacb985e3d9c3db3d55d01
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52398332"
---
# <a name="international-features-of-the-jdbc-driver"></a>Caractéristiques internationales du pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] offre les fonctionnalités d’internationalisation suivantes :  
  
-   Prise en charge d’une version complètement localisée dans les mêmes langues que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Prise en charge des conversions de langage Java pour les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sensibles aux paramètres régionaux  
  
-   Prise en charge des langues internationales, quel que soit le système d’exploitation  
  
-   Prise en charge des noms de domaine internationaux (à compter du pilote Microsoft JDBC 6.0 pour SQL Server)  
  
## <a name="handling-of-character-data"></a>Gestion des données caractères  
 Les données de type caractère dans Java sont traitées par défaut en tant qu’Unicode ; l’objet Java **String**représente des données de type caractère Unicode. Dans le pilote JDBC, les méthodes getter et setter du flux de données ASCII constituent la seule exception à cette règle ; il s'agit de cas à part, car ces méthodes utilisent des flux d'octets en se basant sur l'hypothèse implicite de pages de codes uniques et bien connues (ASCII).  
  
 En outre, le pilote JDBC fournit la **sendStringParametersAsUnicode** propriété chaîne de connexion. Cette propriété peut être utilisée pour spécifier que les paramètres préparés pour les données caractères sont envoyés en tant que caractères ASCII ou en tant que jeu de caractères multioctets (MBCS), et non en tant que caractères Unicode. Pour plus d’informations sur la **sendStringParametersAsUnicode** propriété de chaîne de connexion, consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
### <a name="driver-incoming-conversions"></a>Conversions entrantes du pilote  
 Les données de type texte Unicode provenant du serveur ne doivent pas être converties. Elles sont transmises directement en Unicode. Les données non-Unicode provenant du serveur sont converties en Unicode à partir de la page de codes des données, au niveau base de données ou colonne. Le pilote JDBC utilise les routines de conversion de machine virtuelle Java (Java Virtual Machine, JVM) pour effectuer ces conversions. Ces conversions sont effectuées sur toutes les méthodes getter des flux de données de type chaînes et caractères.  
  
 Si la machine virtuelle Java (JVM) ne prend pas en charge la page de codes appropriée pour les données de la base de données, le pilote JDBC lève l'exception suivante : « Page de codes XXX non prise en charge par l'environnement Java ». Pour résoudre ce problème, vous devez installer la prise en charge complète des caractères internationaux requise par cette machine virtuelle Java. Pour obtenir un exemple, consultez la documentation relative aux encodages pris en charge sur le site Web de Sun Microsystems.  
  
### <a name="driver-outgoing-conversions"></a>Conversions sortantes du pilote  
 Les données caractères allant du pilote au serveur peuvent être au format ASCII ou Unicode. Par exemple, les nouvelles méthodes JDBC 4.0 prenant en charge les caractères nationaux, comme les méthodes setNString, setNCharacterStream et setNClob des classes [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), envoient toujours leurs valeurs de paramètres au serveur au format Unicode.  
  
 Par ailleurs, les méthodes d’API basées sur des caractères non nationaux, comme les méthodes setString, setCharacterStream et setClob methods des classes [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), envoient leurs valeurs au serveur au format Unicode seulement quand la propriété **sendStringParametersAsUnicode** est définie sur « true », qui est la valeur par défaut.  
  
## <a name="non-unicode-parameters"></a>Paramètres non Unicode  
 Pour des performances optimales avec **CHAR**, **VARCHAR** ou **LONGVARCHAR** type de paramètres non Unicode, définissez le **sendStringParametersAsUnicode** connexion propriété sur « false » de type chaîne et utiliser les méthodes des caractères non nationaux.  
  
## <a name="formatting-issues"></a>Problèmes de mise en forme  
 Pour les dates, les heures et les devises, toute la mise en forme des données localisées est effectuée au niveau du langage Java avec l’objet Locale, et les différentes méthodes de mise en forme pour les types de données **Date**, **Calendar** et **Number**. Dans le cas, rare, où le pilote JDBC doit passer des données sensibles respectant les paramètres régionaux dans un format localisé, le programme approprié de mise en forme est utilisé avec les paramètres régionaux par défaut de la machine virtuelle Java.  
  
## <a name="collation-support"></a>Prise en charge du classement  
 Le pilote JDBC version 3.0 prend en charge tous les classements pris en charge par [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] et [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ainsi que les nouveaux classements ou les nouvelles versions des noms de classements Windows introduits dans [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
 Pour plus d’informations sur les classements, consultez [Prise en charge d’Unicode et du classement](https://go.microsoft.com/fwlink/?LinkId=131366) et [Nom de classement Windows (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=131367) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="using-international-domain-names-idn"></a>Utilisation de noms de domaine internationaux (IDN)  
 Le pilote JDBC 6.0 pour SQL Server prend en charge l’utilisation de noms de domaine internationaux et peut convertir un nom de serveur Unicode en codage compatible avec le format ASCII (Punycode) si nécessaire pendant une connexion.  Si les noms de domaines internationaux sont stockés dans le système DNS (Domain Name System) en tant que chaînes ASCII au format Punycode (spécifié par la RFC 3490), activez la conversion du nom de serveur Unicode en affectant la valeur « True » à la propriété serverNameAsACE.  Sinon, si le service DNS est configuré pour autoriser l’utilisation de caractères Unicode, affectez la valeur « false » (valeur par défaut) à la propriété serverNameAsACE.  Pour les versions antérieures du pilote JDBC, vous pouvez aussi convertir le nom du serveur au format Punycode avec les méthodes [IDN.toASCII de Java](https://docs.oracle.com/javase/8/docs/api/java/net/IDN.html) avant de définir cette propriété pour une connexion.  
  
> [!NOTE]  
>  La plupart des logiciels de résolution écrits pour les plateformes autres que Windows sont basés sur les normes DSN Internet. Il est donc plus probable qu’ils utilisent le format Punycode pour les noms de domaines internationaux, alors qu’un serveur DNS Windows sur un réseau privé peut être configuré pour autoriser l’utilisation des caractères UTF-8 en fonction du serveur.  Pour plus d’informations, consultez [Prise en charge des caractères Unicode](https://technet.microsoft.com/library/cc738403(v=ws.10).aspx).  
  
## <a name="see-also"></a> Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
