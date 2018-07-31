---
title: Wrappers et Interfaces | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 27fc9b72-9f21-4728-abcb-5c015f28a6ab
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a96d9b11473171cabd40e485342e1846017b307
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279230"
---
# <a name="wrappers-and-interfaces"></a>Wrappers et interfaces
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge les interfaces qui permettent de créer un proxy d’une classe, ainsi que les wrappers qui permettent d’accéder à des extensions de l’API JDBC propres au [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] par le biais d’une interface proxy.  
  
## <a name="wrappers"></a>Wrappers  
 Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge l’interface java.sql.Wrapper. Cette interface fournit un mécanisme d’accès aux extensions de l’API JDBC qui sont propres au [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] par le biais d’une interface proxy.  
  
 L’interface java.sql.Wrapper définit deux méthodes : **isWrapperFor** et **unwrap**. La méthode **isWrapperFor** vérifie si l’objet d’entrée spécifié implémente cette interface. La méthode **unwrap** retourne un objet qui implémente cette interface afin d’autoriser l’accès aux méthodes propres au [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 **isWrapperFor** et **unwrap** méthodes sont exposées comme suit :  
  
-   [isWrapperFor, méthode &#40;SQLServerCallableStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)  
  
-   [unwrap, méthode &#40;SQLServerCallableStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)  
  
-   [isWrapperFor, méthode &#40;SQLServerConnectionPoolDataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverconnectionpooldatasource.md)  
  
-   [unwrap, méthode &#40;SQLServerConnectionPoolDataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)  
  
-   [isWrapperFor, méthode &#40;SQLServerDataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)  
  
-   [Méthode Unwrap &#40;SQLServerDataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)  
  
-   [isWrapperFor, méthode &#40;SQLServerPreparedStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)  
  
-   [unwrap, méthode &#40;SQLServerPreparedStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)  
  
-   [isWrapperFor, méthode &#40;SQLServerStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)  
  
-   [Méthode Unwrap &#40;SQLServerStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)  
  
-   [isWrapperFor, méthode &#40;SQLServerXADataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md)  
  
-   [Méthode Unwrap &#40;SQLServerXADataSource&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)  
  
## <a name="interfaces"></a>Interfaces  
 À compter de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] JDBC Driver 3.0, des interfaces sont disponibles pour qu’un serveur d’applications accède à une méthode propre au pilote à partir de la classe associée. Le serveur d’applications peut encapsuler la classe en créant un proxy, exposant la fonctionnalité propre au [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] à partir d’une interface. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge les interfaces disposant des méthodes et constantes propres au [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], de sorte qu’un serveur d’applications puisse créer un proxy de la classe.  
  
 Les interfaces sont dérivées d’interfaces Java standard. Par conséquent, vous pouvez utiliser le même objet une fois qu’il est désencapsulé pour accéder à la fonctionnalité générique ou à celle propre au [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 Les interfaces suivantes ont été ajoutées :  
  
-   [ISQLServerCallableStatement](../../connect/jdbc/reference/isqlservercallablestatement-interface.md)  
  
-   [ISQLServerConnection](../../connect/jdbc/reference/isqlserverconnection-interface.md)  
  
-   [ISQLServerDataSource](../../connect/jdbc/reference/isqlserverdatasource-interface.md)  
  
-   [ISQLServerPreparedStatement](../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
-   [ISQLServerResultSet](../../connect/jdbc/reference/isqlserverresultset-interface.md)  
  
-   [ISQLServerStatement](../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="example"></a> Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre comment accéder à une fonctionnalité propre au [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] à partir d’un objet DataSource. Cette classe DataSource peut avoir été encapsulée par un serveur d’applications. Pour accéder à la fonctionnalité ou constante propre au pilote JDBC, vous pouvez désencapsuler la source de données dans une interface ISQLServerDataSource et utiliser les fonctionnalités déclarées dans cette interface.  
  
### <a name="code"></a>Code  
  
```java
import javax.sql.*;  
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class UnWrapTest {  
   public static void main(String[] args) {  
      // This is a test.  This DataSource object could be something from an appserver   
      // which has wrapped the real SQLServerDataSource with its own wrapper  
      SQLServerDataSource ds = new SQLServerDataSource();  
      checkSendStringParametersAsUnicode(ds);  
   }  
  
   // Unwrap to the ISQLServerDataSource interface to access the getSendStringParametersAsUnicode function  
   static void checkSendStringParametersAsUnicode(DataSource ds) {  
      try {  
         final ISQLServerDataSource sqlServerDataSource = ds.unwrap(ISQLServerDataSource.class);  
         boolean sendStringParametersAsUnicode = sqlServerDataSource.getSendStringParametersAsUnicode();  
  
         System.out.println("Send string as parameter value is:-" + sendStringParametersAsUnicode);  
  
      } catch (SQLException sqlE) {  
         System.out.println("Exception:-" + sqlE);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
