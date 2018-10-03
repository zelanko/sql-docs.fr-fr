---
title: Informations de référence sur l’API Always Encrypted pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 691e1c573e2f96c0727970fac858bcfe761d22fc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47831067"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Informations de référence sur l’API Always Encrypted pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le Chiffrement intégral permet aux clients de chiffrer des données sensibles dans des applications clientes et de ne jamais révéler les clés de chiffrement à SQL Server. À cette fin, un pilote Always Encrypted installé sur l’ordinateur client chiffre et déchiffre automatiquement les données sensibles dans l’application cliente SQL Server. Le pilote chiffre les données dans les colonnes sensibles avant de les transmettre à SQL Server et il réécrit automatiquement les requêtes pour que la sémantique de l’application soit conservée. De même, il déchiffre de façon transparente les données stockées dans les colonnes de base de données chiffrées qui figurent dans les résultats des requêtes. Pour plus d’informations, consultez [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) et [à l’aide de Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted est pris en charge uniquement par le pilote Microsoft JDBC 6.0 ou ultérieur pour SQL Server avec SQL Server 2016.  
  
 ## <a name="always-encrypted-api-references"></a>Informations de référence sur l’API Always Encrypted
 
 Plusieurs ajouts et modifications ont été apportés à l’API du pilote JDBC pour une utilisation dans les applications clientes qui utilisent Always Encrypted.  
  
 **SQLServerConnection, classe**  
  
|Nom   |Description|  
|----------|-----------------|  
|Nouveau mot clé de chaîne de connexion :<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled active la fonctionnalité Always Encrypted pour la connexion, et columnEncryptionSetting=Disabled la désactive. Les valeurs acceptées sont Enabled/Disabled. La valeur par défaut est Disabled.|  
|Nouvelles méthodes :<br /><br /> `public static void setColumnEncryptionTrustedMasterKeyPaths(Map<String, List\<String>> trustedKeyPaths)`<br /><br /> `public static void updateColumnEncryptionTrustedMasterKeyPaths(String server, List\<String> trustedKeyPaths)`<br /><br /> `public static void removeColumnEncryptionTrustedMasterKeyPaths(String server)`|Vous permet de définir/mettre à jour/supprimer une liste de chemins de clés approuvés pour un serveur de bases de données. Si pendant le traitement d’une requête d’application, le pilote reçoit un chemin de clé qui ne figure pas dans la liste, la requête échoue. Cette propriété fournit une protection supplémentaire contre les attaques de sécurité au cours desquelles un ordinateur SQL Server compromis envoie des chemins de clés factices, qui peuvent entraîner une fuite des informations d’identification du magasin de clés.|  
|Nouvelle méthode :<br /><br /> `public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()`|Retourne une liste de chemins d’accès de clés approuvés pour un serveur de bases de données.|  
|Nouvelle méthode :<br /><br /> `public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)`|Vous permet d’inscrire des fournisseurs de magasins de clés personnalisés. Il s’agit d’un dictionnaire qui mappe des noms de fournisseurs de magasins de clés à des implémentations de fournisseurs de magasins de clés.<br /><br /> Pour utiliser le magasin de clés JVM, vous devez instancier un objet SQLServerColumnEncryptionJVMKeyStoreProvider avec des informations d’identification du magasin de clés JVM et l’inscrire auprès du pilote. Le nom de ce fournisseur doit être « MSSQL_JVM_KEYSTORE ».<br /><br /> Pour utiliser le magasin de Azure Key Vault, vous devez instancier un objet SQLServerColumnEncryptionAzureKeyStoreProvider et l’inscrire auprès du pilote. Le nom de ce fournisseur doit être « AZURE_KEY_VAULT ».|
|`public final boolean getSendTimeAsDatetime()`|Retourne le paramètre de la propriété de connexion sendTimeAsDatetime.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)`|Modifie le paramètre de la propriété de connexion sendTimeAsDatetime.|

 **Classe de SQLServerConnectionPoolProxy**
|Nom   |Description|  
|----------|-----------------|  
|`public final boolean getSendTimeAsDatetime()` | Retourne le paramètre de la propriété de connexion sendTimeAsDatetime.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)` | Modifie le paramètre de la propriété de connexion sendTimeAsDatetime.|
     
  
 **SQLServerDataSource, classe**  
  
|Nom   |Description|  
|----------|-----------------|  
|`public void setColumnEncryptionSetting(String columnEncryptionSetting)`|Active/désactive la fonctionnalité Always Encrypted pour l’objet de source de données.<br /><br /> La valeur par défaut est Disabled.|  
|`public String getColumnEncryptionSetting()`|Récupère le paramètre de fonctionnalité Always Encrypted pour l’objet de source de données.|
|`public void setKeyStoreAuthentication(String keyStoreAuthentication)`|Définit le nom qui identifie un magasin de clés. Seule valeur prise en charge est la **JavaKeyStorePassword** pour identifier le Store de clé Java.<br/><br/>La valeur par défaut est null.|
|`public String getKeyStoreAuthentication()`|Obtient la valeur du paramètre keyStoreAuthentication pour l’objet de source de données.|
|`public void setKeyStoreSecret(String keyStoreSecret)`|Définit le mot de passe pour le magasin de clés Java. Le mot de passe pour le magasin de clés et la clé doit être identiques. Notez que keyStoreAuthentication doit être définie avec **JavaKeyStorePassword**.|
|`public void setKeyStoreLocation(String keyStoreLocation)`|Définit l’emplacement, y compris le nom de fichier pour le magasin de clés Java. Notez que keyStoreAuthentication doit être définie avec **JavaKeyStorePassword**.|
|`public String getKeyStoreLocation()`|Récupère la keyStoreLocation pour le Store de clé Java.|
  
 **Classe de SQLServerColumnEncryptionJavaKeyStoreProvider**  
  
 Implémentation du fournisseur de magasins de clés pour le magasin de clés Java. Cette classe permet d’utiliser des certificats stockés dans le magasin de clés Java comme clés principales de colonne.  
  
 Constructeurs  
  
|Nom   |Description|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionJavaKeyStoreProvider (String keyStoreLocation, char[] keyStoreSecret)`|Fournisseur de magasin de clés pour le Store de clé Java.|  
  
 Méthodes  
  
|Nom   |Description|  
|----------|-----------------|  
|`public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)`|Déchiffre la valeur chiffrée spécifiée d’une clé CEK. La valeur chiffrée est censée être chiffrée à l’aide du certificat avec le chemin d’accès de clé spécifié et à l’aide de l’algorithme spécifié.<br /><br /> **Le format du chemin de clé doit être un des suivants :**<br /><br /> Thumbprint:<empreinte_certificate><br /><br /> Alias:<alias_certificat><br /><br /> (Remplace SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (String, String, Byte[]).)|  
|`public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)`|Chiffre une clé CEK à l’aide du certificat avec le chemin d’accès de clé spécifié et à l’aide de l’algorithme spécifié.<br /><br /> **Le format du chemin de clé doit être un des suivants :**<br /><br /> Thumbprint:<empreinte_certificate><br /><br /> Alias:<alias_certificat><br /><br /> (Remplace SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (String, String, Byte[]).)|  
|`public void setName (String name)`|Définit le nom de ce fournisseur de magasin de clés.|
|`public String getName ()`|Obtient le nom de ce fournisseur de magasin de clés.|
  
 **Classe de SQLServerColumnEncryptionAzureKeyVaultProvider**  
  
 Implémentation du fournisseur de magasins de clés pour Azure Key Vault. Cette classe permet à l’aide des clés stockées dans Azure Key Vault en tant que clés principales de colonne.  
  
 Constructeurs  
  
|Nom   |Description|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionAzureKeyVaultProvider (String clientId, String clientKey)`|Fournisseur de magasin de clés pour Azure Key Vault.  Vous devez fournir l’identificateur et la clé du client demande le jeton pour s’authentifier auprès d’Azure Key Vault.|  
  
 Méthodes  
  
|Nom   |Description|  
|----------|-----------------|  
| `public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)` | Decryptes une clé de chiffrement de colonne chiffrée (CEK). Ce déchiffrement est effectué avec un algorithme de chiffrement RSA qui utilise la clé asymétrique spécifiée par le chemin d’accès de la clé principale.<br />(Remplace SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (String, String, Byte[]).) |  
| `public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)` | Chiffre une clé de chiffrement de colonne, en donnant la clé principale de colonne spécifiée à l’algorithme spécifié.<br />(Remplace SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (String, String, Byte[]).) |  
|`public void setName (String name)`|Définit le nom de ce fournisseur de magasin de clés.|
|`public String getName ()`|Obtient le nom de ce fournisseur de magasin de clés.|  
  
  
 **Interface de SQLServerKeyVaultAuthenticationCallback**  
  
 Cette interface contient une méthode pour l’authentification Azure Key Vault, ce qui doit être implémentée par l’utilisateur.  
  
 Méthodes  
  
|Nom   |Description|  
|----------|-----------------|  
|`public String getAccessToken(String authority, String resource, String scope);`|La méthode doit être substituée. La méthode est utilisée pour obtenir un jeton à Azure Key Vault accès.|  
  
 **SQLServerColumnEncryptionKeyStoreProvider Class**  
  
 Étendez cette classe pour implémenter un fournisseur de magasins de clés personnalisé.  
  
|Nom   |Description|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Classe de base pour tous les fournisseurs de magasins de clés. Un fournisseur personnalisé doit dériver de cette classe et remplacer ses fonctions membres, puis l’inscrire avec SQLServerConnection. registerColumnEncryptionKeyStoreProviders().|  
  
 Méthodes  
  
|Nom   |Description|  
|----------|-----------------|  
|`public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)`|Méthode de classe de base pour déchiffrer la valeur chiffrée spécifiée d’une clé CEK. La valeur chiffrée doit être chiffrée en utilisant la clé principale de colonne avec le chemin de clé spécifié et l’algorithme spécifié.|  
|`public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)`|Méthode de classe de base pour chiffrer une clé CEK à l’aide de la clé CMK avec le chemin d’accès de clé spécifié et à l’aide de l’algorithme spécifié.|
|`public abstract void setName(String name)`|Définit le nom de ce fournisseur de magasin de clés.|
|`public abstract String getName()`|Obtient le nom de ce fournisseur de magasin de clés.|  
  
 Méthodes nouvelles ou surchargés dans **SQLServerPreparedStatement** classe  
  
|Nom   |Description|  
|----------|-----------------|  
|`public void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale)`<br /><br /> `public void setTime(int parameterIndex, java.sql.Time x, int scale)`<br /><br /> `public void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale)` <br />`public void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale)`|Ces méthodes sont surchargées avec une précision ou un argument d’échelle ou les deux pour prendre en charge d’Always Encrypted pour les types de données spécifiques qui nécessitent une précision et l’échelle d’informations.|  
|`public void setMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setSmallMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setUniqueIdentifier(int parameterIndex, String guid)`<br /><br /> `public void setDateTime(int parameterIndex, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(int parameterIndex, java.sql.Timestamp x)`|Ces méthodes sont ajoutées pour prendre en charge d’Always Encrypted de types de données money, smallmoney, uniqueidentifier, datetime et smalldatetime. <br/><br/>Notez qu’existant `setTimestamp()` méthode est utilisée pour envoyer des valeurs de paramètre dans la colonne chiffrée datetime2. Pour les colonnes datetime et smalldatetime chiffrées, utilisez les nouvelles méthodes `setDateTime()` et `setSmallDateTime()` respectivement.|  
|`public final void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setSmallMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setBoolean(int parameterIndex, boolean x, boolean forceEncrypt)`<br /><br /> `public final void setByte(int parameterIndex, byte x, boolean forceEncrypt)`<br /><br /> `public final void setBytes(int parameterIndex, byte x[], boolean forceEncrypt)`<br /><br /> `public final void setUniqueIdentifier(int parameterIndex, String guid, boolean forceEncrypt)`<br /><br /> `public final void setDouble(int parameterIndex, double x, boolean forceEncrypt)`<br /><br /> `public final void setFloat(int parameterIndex, float x, boolean forceEncrypt)`<br /><br /> `public final void setInt(int parameterIndex, int value, boolean forceEncrypt)`<br /><br /> `public final void setLong(int parameterIndex, long x, boolean forceEncrypt)`<br /><br /> `public final setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale, boolean forceEncrypt)`<br /><br /> `public final void setShort(int parameterIndex, short x, boolean forceEncrypt)`<br /><br /> `public final void setString(int parameterIndex, String str, boolean forceEncrypt)`<br /><br /> `public final void setNString(int parameterIndex, String value, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setSmallDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setDate(int parameterIndex, java.sql.Date x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, java.util.Calendar cal, boolean forceEncrypt)`|Définit le paramètre désigné sur la valeur Java donnée.<br /><br /> Si le forceEncrypt booléenne est définie sur true, la requête paramètre sera uniquement être défini si la désignation de colonne est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction.<br /><br /> Si le forceEncrypt booléenne est définie sur false, le pilote ne sont pas forcer le chiffrement sur les paramètres.|  
  
 Méthodes nouvelles ou surchargés dans **SQLServerCallableStatement** classe  
  
|Nom   |Description|  
|----------|-----------------|  
|`public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)`<br />`public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale)`<br/><br/>`public final void setObject(String sCol, Object x, int targetSqlType, Integer precision, int scale)`|Ces méthodes sont surchargées avec une précision ou un argument d’échelle ou les deux pour prendre en charge d’Always Encrypted pour les types de données spécifiques qui nécessitent une précision et l’échelle d’informations.|  
|`public void setDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid)`<br /><br /> `public void setMoney(String parameterName, BigDecimal bd)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd)`<br/><br/>`public Timestamp getDateTime(int index)`<br/><br/>`public Timestamp getDateTime(String sCol)`<br/><br/>`public Timestamp getDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(int index)`<br/><br/>`public Timestamp getSmallDateTime(String sCol)`<br/><br/>`public Timestamp getSmallDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(String name, Calendar cal)`<br/><br/>`public BigDecimal getMoney(int index)`<br/><br/>`public BigDecimal getMoney(String sCol)`<br/><br/>`public BigDecimal getSmallMoney(int index)`<br/><br/>`public BigDecimal getSmallMoney(String sCol)`|Ces méthodes sont ajoutées pour prendre en charge d’Always Encrypted de types de données money, smallmoney, uniqueidentifier, datetime et smalldatetime. <br/><br/>Notez qu’existant `setTimestamp()` méthode est utilisée pour envoyer des valeurs de paramètre dans la colonne chiffrée datetime2. Pour les colonnes datetime et smalldatetime chiffrées, utilisez les nouvelles méthodes `setDateTime()` et `setSmallDateTime()` respectivement.|  
|`public void setObject(String parameterName, Object o, int n, int m, boolean forceEncrypt)`<br /><br /> `public void setObject(String parameterName, Object obj, SQLType jdbcType, int scale, boolean forceEncrypt)`<br /><br /> `public void setDate(String parameterName, java.sql.Date x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale, boolean forceEncrypt)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid, boolean forceEncrypt)`<br /><br /> `public void setBytes(String parameterName, byte[] b, boolean forceEncrypt)`<br /><br /> `public void setByte(String parameterName, byte b, boolean forceEncrypt)`<br /><br /> `public void setString(String parameterName, String s, boolean forceEncrypt)`<br /><br /> `public final void setNString(String parameterName, String value, boolean forceEncrypt)<br /><br /> public void setMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public void setDouble(String parameterName, double d, boolean forceEncrypt)`<br /><br /> `public void setFloat(String parameterName, float f, boolean forceEncrypt)`<br /><br /> `public void setInt(String parameterName, int i, boolean forceEncrypt)`<br /><br /> `public void setLong(String parameterName, long l, boolean forceEncrypt)`<br /><br /> `public void setShort(String parameterName, short s, boolean forceEncrypt)`<br /><br /> `public void setBoolean(String parameterNames, boolean b, boolean forceEncrypt)`<br/><br/>`public void setTimeStamp(String sCol, java.sql.Timestamp x, Calendar c, Boolean forceEncrypt)`|Définit le paramètre désigné sur la valeur Java donnée.<br /><br /> Si le forceEncrypt booléenne est définie sur true, la requête paramètre sera uniquement être défini si la désignation de colonne est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction.<br /><br /> Si le forceEncrypt booléenne est définie sur false, le pilote ne sont pas forcer le chiffrement sur les paramètres.|
 

 Méthodes nouvelles ou surchargés dans **SQLServerResultSet** classe  
  
|Nom   |Description|  
|----------|-----------------|  
|`public String getUniqueIdentifier(int columnIndex)`<br/><br/>`public String getUniqueIdentifier(String columnLabel)`<br/><br/>   `public java.sql.Timestamp getDateTime(int columnIndex)` <br/><br/> `public java.sql.Timestamp getDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getDateTime(int columnIndex, Calendar cal)`   <br/><br/>`public java.sql.Timestamp getDateTime(String colName, Calendar cal)`    <br/><br/>`public java.sql.Timestamp getSmallDateTime(int columnIndex)`    <br/><br/> `public java.sql.Timestamp getSmallDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(int columnIndex, Calendar cal)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(String colName, Calendar cal)`   <br/><br/>  `public BigDecimal getMoney(int columnIndex)`  <br/><br/> `public BigDecimal getMoney(String columnName)`   <br/><br/> `public BigDecimal getSmallMoney(int columnIndex)`   <br/><br/>  `public BigDecimal getSmallMoney(String columnName)`  <br/><br/>`public void updateMoney(String columnName, BigDecimal x)`    <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x)`  <br/><br/>     `public void updateDateTime(int index, java.sql.Timestamp x)` <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x)` |Ces méthodes sont ajoutées pour prendre en charge d’Always Encrypted pour types de données money, smallmoney, uniqueidentifier, datetime et smalldatetime. <br/><br/>Notez qu’existant `updateTimestamp()` méthode est utilisée pour la mise à jour des colonnes datetime2 chiffré. Pour les colonnes datetime et smalldatetime chiffrées, utilisez les nouvelles méthodes `updateDateTime()` et `updateSmallDateTime()` respectivement.|
|`public void updateBoolean(int index, boolean x, boolean forceEncrypt)`  <br/><br/>  `public void updateByte(int index, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(int index, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(int index, int x, boolean forceEncrypt)`   <br/><br/>  `public void updateLong(int index, long x, boolean forceEncrypt)`  <br/><br/> `public void updateFloat(int index, float x, boolean forceEncrypt)`   <br/><br/> `public void updateDouble(int index, double x, boolean forceEncrypt)`   <br/><br/> `public void updateMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateSmallMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateBigDecimal(int index, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateString(int columnIndex, String stringValue, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(int columnIndex, String nString, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(String columnLabel, String nString, boolean forceEncrypt)`  <br/><br/> `public void updateBytes(int index, byte x[], boolean forceEncrypt)   <br/><br/>  public void updateDate(int index, java.sql.Date x, boolean forceEncrypt)`  <br/><br/> `public void updateTime(int index, java.sql.Time x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateTimestamp(int index, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/> `public void updateDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateUniqueIdentifier(int index, String x, boolean forceEncrypt)`    <br/><br/>  `public void updateObject(int index, Object x, int precision, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateObject(int index, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateBoolean(String columnName, boolean x, boolean forceEncrypt)`    <br/><br/>  `public void updateByte(String columnName, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(String columnName, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(String columnName, int x, boolean forceEncrypt)`   <br/><br/>   `public void updateLong(String columnName, long x, boolean forceEncrypt)` <br/><br/>  `public void updateFloat(String columnName, float x, boolean forceEncrypt)`  <br/><br/>  `public void updateDouble(String columnName, double x, boolean forceEncrypt)  <br/><br/> public void updateBigDecimal(String columnName, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateBigDecimal(String columnName, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateString(String columnName, String x, boolean forceEncrypt)`   <br/><br/>  `public void updateBytes(String columnName, byte x[], boolean forceEncrypt)`  <br/><br/> `public void updateDate(String columnName, java.sql.Date x, boolean forceEncrypt)`   <br/><br/>  `public void updateTime(String columnName, java.sql.Time x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateTimestamp(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateDateTimeOffset(String columnName, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateUniqueIdentifier(String columnName, String x, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object x, int precision, int scale, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`|Mettre à jour la colonne désignée à la valeur java donnée.<br/><br/>Si le forceEncrypt booléenne est définie sur true, la colonne n’a la valeur si elle est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction.<br/><br/>Si le forceEncrypt booléenne est définie sur false, le pilote ne sont pas forcer le chiffrement sur les paramètres.|

  
Nouveaux types dans **microsoft.sql.Types** classe
|Nom   |Description|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Utiliser ces types en tant que types SQL cibles lors de l’envoi des valeurs de paramètre à **chiffrées** datetime, smalldatetime, money, smallmoney, les colonnes uniqueidentifier à l’aide de `setObject()/updateObject()` méthodes d’API.|  
  
  
 **SQLServerStatementColumnEncryptionSetting Enum**  
  
 Spécifie comment les données sont envoyées et reçues lors de la lecture et l’écriture des colonnes chiffrées. Selon votre requête spécifique, impact sur les performances peut-être être réduites en contournant le pilote Always Encrypted traitement lorsque les colonnes non chiffrées sont utilisés. Notez que ces paramètres ne peuvent pas être utilisés pour contourner le chiffrement et accéder aux données de texte en clair.  
  
 **Syntaxe**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Membres**  
  
|Nom   |Description|  
|----------|-----------------|  
|UseConnectionSetting|Spécifie que la commande doit utiliser par défaut le paramètre Always Encrypted dans la chaîne de connexion.|  
|Activé|Active Always Encrypted pour la requête.|  
|ResultSetOnly|Spécifie que seuls les résultats de la commande doivent être traités par la routine Always Encrypted dans le pilote. Utilisez cette valeur lors de la commande n’a aucun paramètre qui exigent un chiffrement.|  
|Désactivé|Désactive Always Encrypted pour la requête.|  
  
 Le paramètre de niveau instruction pour AE est ajouté à la classe SQLServerConnection et à la classe SQLServerConnectionPoolProxy. Les méthodes suivantes dans ces classes sont surchargées avec le nouveau paramètre.  
  
|Nom   |Description|  
|----------|-----------------|  
|`public Statement createStatement(int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crée un objet d’instruction qui génère des objets de jeu de résultats avec le type donné, d’accès concurrentiel, mise en attente et paramètre de chiffrement de colonne.|  
|`public CallableStatement prepareCall(String sql, int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)`|Crée un objet de CallableStatement avec le paramètre de chiffrement de colonne donné qui génère des objets de jeu de résultats avec le type donné, d’accès concurrentiel et mise en attente.|  
|`public PreparedStatement prepareStatement(String sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donné qui a la possibilité de récupérer les clés générées automatiquement.|  
|`public PreparedStatement prepareStatement(String sql, String[] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donnée qui génère des objets de jeu de résultats avec les noms de colonne donnée.|  
|`public PreparedStatement prepareStatement(String sql, int[] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting`|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donnée qui génère des objets de jeu de résultats avec les index de colonne donné.|  
|`public PreparedStatement prepareStatement(String sql, int nType, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donné qui génère des objets de jeu de résultats avec le type donné, d’accès concurrentiel et mise en attente.|  
  
> [!NOTE]  
>  Si Always Encrypted est désactivé pour une requête et la requête avec des paramètres qui doivent être chiffrées (les paramètres qui correspondent aux colonnes chiffrées), la requête échoue.  
>   
>  Si Always Encrypted est désactivé pour une requête et la requête retourne des résultats à partir des colonnes chiffrées, la requête retournera les valeurs chiffrées. Les valeurs chiffrées aura le type de données varbinary.  
  
 ## <a name="see-also"></a> Voir aussi  
 [Utilisation du chiffrement intégral avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

