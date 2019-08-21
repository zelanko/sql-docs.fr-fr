---
title: Informations de référence sur l'API Always Encrypted pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 79cf8ce1b951621d58105d18b847306ff620d114
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028486"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Informations de référence sur l'API Always Encrypted pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le Chiffrement intégral permet aux clients de chiffrer des données sensibles dans des applications clientes et de ne jamais révéler les clés de chiffrement à SQL Server. À cette fin, un pilote Always Encrypted installé sur l’ordinateur client chiffre et déchiffre automatiquement les données sensibles dans l’application cliente SQL Server. Le pilote chiffre les données dans les colonnes sensibles avant de les transmettre à SQL Server et il réécrit automatiquement les requêtes pour que la sémantique de l’application soit conservée. De même, il déchiffre de façon transparente les données stockées dans les colonnes de base de données chiffrées qui figurent dans les résultats des requêtes. Pour plus d’informations, consultez [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) et [utilisation de Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted est pris en charge uniquement par le pilote Microsoft JDBC 6.0 ou ultérieur pour SQL Server avec SQL Server 2016.  
  
 ## <a name="always-encrypted-api-references"></a>Informations de référence sur l'API Always Encrypted
 
 Plusieurs ajouts et modifications ont été apportés à l’API du pilote JDBC pour une utilisation dans les applications clientes qui utilisent Always Encrypted.  
  
 **Classe SQLServerConnection**  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|Nouveau mot clé de chaîne de connexion :<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled active la fonctionnalité Always Encrypted pour la connexion, et columnEncryptionSetting=Disabled la désactive. Les valeurs acceptées sont Enabled/Disabled. La valeur par défaut est Disabled.|  
|Nouvelles méthodes :<br /><br /> `public static void setColumnEncryptionTrustedMasterKeyPaths(Map<String, List\<String>> trustedKeyPaths)`<br /><br /> `public static void updateColumnEncryptionTrustedMasterKeyPaths(String server, List\<String> trustedKeyPaths)`<br /><br /> `public static void removeColumnEncryptionTrustedMasterKeyPaths(String server)`|Vous permet de définir/mettre à jour/supprimer une liste de chemins de clés approuvés pour un serveur de bases de données. Si pendant le traitement d’une requête d’application, le pilote reçoit un chemin de clé qui ne figure pas dans la liste, la requête échoue. Cette propriété fournit une protection supplémentaire contre les attaques de sécurité au cours desquelles un ordinateur SQL Server compromis envoie des chemins de clés factices, qui peuvent entraîner une fuite des informations d’identification du magasin de clés.|  
|Nouvelle méthode :<br /><br /> `public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()`|Retourne une liste de chemins d’accès de clés approuvés pour un serveur de bases de données.|  
|Nouvelle méthode :<br /><br /> `public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)`|Vous permet d’inscrire des fournisseurs de magasins de clés personnalisés. Il s’agit d’un dictionnaire qui mappe des noms de fournisseurs de magasins de clés à des implémentations de fournisseurs de magasins de clés.<br /><br /> Pour utiliser le magasin de clés JVM, vous devez instancier un objet SQLServerColumnEncryptionJVMKeyStoreProvider avec des informations d’identification du magasin de clés JVM et l’inscrire auprès du pilote. Le nom de ce fournisseur doit être « MSSQL_JVM_KEYSTORE ».<br /><br /> Pour utiliser le magasin de Azure Key Vault, vous devez instancier un objet SQLServerColumnEncryptionAzureKeyStoreProvider et l’inscrire auprès du pilote. Le nom de ce fournisseur doit être «AZURE_KEY_VAULT».|
|`public final boolean getSendTimeAsDatetime()`|Retourne le paramètre de la propriété de connexion sendTimeAsDatetime.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)`|Modifie le paramètre de la propriété de connexion sendTimeAsDatetime.|

 **Classe SQLServerConnectionPoolProxy**
 
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public final boolean getSendTimeAsDatetime()` | Retourne le paramètre de la propriété de connexion sendTimeAsDatetime.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)` | Modifie le paramètre de la propriété de connexion sendTimeAsDatetime.|
     
  
 **Classe SQLServerDataSource**  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public void setColumnEncryptionSetting(String columnEncryptionSetting)`|Active/désactive la fonctionnalité Always Encrypted pour l’objet de source de données.<br /><br /> La valeur par défaut est Disabled.|  
|`public String getColumnEncryptionSetting()`|Récupère le paramètre de fonctionnalité Always Encrypted pour l’objet de source de données.|
|`public void setKeyStoreAuthentication(String keyStoreAuthentication)`|Définit le nom qui identifie un magasin de clés. Seule la valeur prise en charge est le **JavaKeyStorePassword** pour identifier le magasin de clés Java.<br/><br/>La valeur par défaut est null.|
|`public String getKeyStoreAuthentication()`|Obtient la valeur du paramètre keyStoreAuthentication pour l’objet source de données.|
|`public void setKeyStoreSecret(String keyStoreSecret)`|Définit le mot de passe pour le magasin de clés Java. Le mot de passe du magasin de clés et la clé doivent être identiques. Notez que keyStoreAuthentication doit être défini avec **JavaKeyStorePassword**.|
|`public void setKeyStoreLocation(String keyStoreLocation)`|Définit l’emplacement, y compris le nom de fichier du magasin de clés Java. Notez que keyStoreAuthentication doit être défini avec **JavaKeyStorePassword**.|
|`public String getKeyStoreLocation()`|Récupère le keyStoreLocation pour le magasin de clés Java.|
  
 **Classe SQLServerColumnEncryptionJavaKeyStoreProvider**  
  
 Implémentation du fournisseur de magasins de clés pour le magasin de clés Java. Cette classe permet d’utiliser des certificats stockés dans le magasin de clés Java comme clés principales de colonne.  
  
 Constructeurs  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionJavaKeyStoreProvider (String keyStoreLocation, char[] keyStoreSecret)`|Fournisseur de magasin de clés pour le magasin de clés Java.|  
  
 Méthodes  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)`|Déchiffre la valeur chiffrée spécifiée d’une clé CEK. La valeur chiffrée est censée être chiffrée à l’aide du certificat avec le chemin d’accès de clé spécifié et à l’aide de l’algorithme spécifié.<br /><br /> **Le format du chemin de clé doit être un des suivants :**<br /><br /> Thumbprint:<empreinte_certificate><br /><br /> Alias:<alias_certificat><br /><br /> (Remplace SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)`|Chiffre une clé CEK à l’aide du certificat avec le chemin d’accès de clé spécifié et à l’aide de l’algorithme spécifié.<br /><br /> **Le format du chemin de clé doit être un des suivants :**<br /><br /> Thumbprint:<empreinte_certificate><br /><br /> Alias:<alias_certificat><br /><br /> (Remplace SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public void setName (String name)`|Définit le nom de ce fournisseur de magasins de clés.|
|`public String getName ()`|Obtient le nom de ce fournisseur de magasins de clés.|
  
 **Classe SQLServerColumnEncryptionAzureKeyVaultProvider**  
  
 Implémentation du fournisseur de magasins de clés pour Azure Key Vault. Cette classe permet l’utilisation de clés stockées dans le Azure Key Vault en tant que clés principales de colonne.  
  
 Constructeurs  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionAzureKeyVaultProvider (String clientId, String clientKey)`|Fournisseur de magasin de clés pour Azure Key Vault.  Vous devez fournir l’identificateur et la clé du client qui demande le jeton pour s’authentifier auprès de Azure Key Vault.|  
  
 Méthodes  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
| `public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)` | Déchiffre une clé de chiffrement de colonne chiffrée (clé CEK). Ce déchiffrement s’effectue à l’aide d’un algorithme de chiffrement RSA qui utilise la clé asymétrique spécifiée par le chemin d’accès de la clé principale.<br />(Remplace SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).) |  
| `public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)` | Chiffre une clé de chiffrement de colonne en donnant à la clé principale de colonne spécifiée l’algorithme spécifié.<br />(Remplace SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).) |  
|`public void setName (String name)`|Définit le nom de ce fournisseur de magasins de clés.|
|`public String getName ()`|Obtient le nom de ce fournisseur de magasins de clés.|  
  
  
 **Interface SQLServerKeyVaultAuthenticationCallback**  
  
 Cette interface contient une méthode pour l’authentification Azure Key Vault, qui doit être implémentée par l’utilisateur.  
  
 Méthodes  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public String getAccessToken(String authority, String resource, String scope);`|La méthode doit être substituée. La méthode est utilisée pour récupérer le jeton d’accès à Azure Key Vault.|  
  
 **Classe SQLServerColumnEncryptionKeyStoreProvider**  
  
 Étendez cette classe pour implémenter un fournisseur de magasins de clés personnalisé.  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Classe de base pour tous les fournisseurs de magasins de clés. Un fournisseur personnalisé doit dériver de cette classe et remplacer ses fonctions membres, puis l’inscrire avec SQLServerConnection. registerColumnEncryptionKeyStoreProviders().|  
  
 Méthodes  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)`|Méthode de classe de base pour déchiffrer la valeur chiffrée spécifiée d’une clé CEK. La valeur chiffrée doit être chiffrée en utilisant la clé principale de colonne avec le chemin de clé spécifié et l’algorithme spécifié.|  
|`public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)`|Méthode de classe de base pour chiffrer une clé CEK à l’aide de la clé CMK avec le chemin d’accès de clé spécifié et à l’aide de l’algorithme spécifié.|
|`public abstract void setName(String name)`|Définit le nom de ce fournisseur de magasins de clés.|
|`public abstract String getName()`|Obtient le nom de ce fournisseur de magasins de clés.|  
  
 Méthodes nouvelles ou surchargées dans la classe **SQLServerPreparedStatement**  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale)`<br /><br /> `public void setTime(int parameterIndex, java.sql.Time x, int scale)`<br /><br /> `public void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale)` <br />`public void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale)`|Ces méthodes sont surchargées avec un argument de précision ou d’échelle, ou pour prendre en charge les Always Encrypted pour des types de données spécifiques qui requièrent des informations de précision et d’échelle.|  
|`public void setMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setSmallMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setUniqueIdentifier(int parameterIndex, String guid)`<br /><br /> `public void setDateTime(int parameterIndex, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(int parameterIndex, java.sql.Timestamp x)`|Ces méthodes sont ajoutées pour prendre en charge Always Encrypted pour les types de données Money, smallmoney, uniqueidentifier, DateTime et smalldatetime. <br/><br/>Notez que la méthode `setTimestamp()` existante est utilisée pour envoyer des valeurs de paramètre à la colonne datetime2 chiffrée. Pour les colonnes DateTime et smalldatetime chiffrées, utilisez les `setDateTime()` nouvelles `setSmallDateTime()` méthodes et, respectivement.|  
|`public final void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setSmallMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setBoolean(int parameterIndex, boolean x, boolean forceEncrypt)`<br /><br /> `public final void setByte(int parameterIndex, byte x, boolean forceEncrypt)`<br /><br /> `public final void setBytes(int parameterIndex, byte x[], boolean forceEncrypt)`<br /><br /> `public final void setUniqueIdentifier(int parameterIndex, String guid, boolean forceEncrypt)`<br /><br /> `public final void setDouble(int parameterIndex, double x, boolean forceEncrypt)`<br /><br /> `public final void setFloat(int parameterIndex, float x, boolean forceEncrypt)`<br /><br /> `public final void setInt(int parameterIndex, int value, boolean forceEncrypt)`<br /><br /> `public final void setLong(int parameterIndex, long x, boolean forceEncrypt)`<br /><br /> `public final setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale, boolean forceEncrypt)`<br /><br /> `public final void setShort(int parameterIndex, short x, boolean forceEncrypt)`<br /><br /> `public final void setString(int parameterIndex, String str, boolean forceEncrypt)`<br /><br /> `public final void setNString(int parameterIndex, String value, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setSmallDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setDate(int parameterIndex, java.sql.Date x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, java.util.Calendar cal, boolean forceEncrypt)`|Définit le paramètre désigné sur la valeur Java donnée.<br /><br /> Si le forceEncrypt booléen a la valeur true, le paramètre de requête est défini uniquement si la colonne de désignation est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction.<br /><br /> Si le forceEncrypt booléen est défini sur false, le pilote ne force pas le chiffrement sur les paramètres.|  
  
 Méthodes nouvelles ou surchargées dans la classe **SQLServerCallableStatement**  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)`<br />`public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale)`<br/><br/>`public final void setObject(String sCol, Object x, int targetSqlType, Integer precision, int scale)`|Ces méthodes sont surchargées avec un argument de précision ou d’échelle, ou pour prendre en charge les Always Encrypted pour des types de données spécifiques qui requièrent des informations de précision et d’échelle.|  
|`public void setDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid)`<br /><br /> `public void setMoney(String parameterName, BigDecimal bd)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd)`<br/><br/>`public Timestamp getDateTime(int index)`<br/><br/>`public Timestamp getDateTime(String sCol)`<br/><br/>`public Timestamp getDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(int index)`<br/><br/>`public Timestamp getSmallDateTime(String sCol)`<br/><br/>`public Timestamp getSmallDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(String name, Calendar cal)`<br/><br/>`public BigDecimal getMoney(int index)`<br/><br/>`public BigDecimal getMoney(String sCol)`<br/><br/>`public BigDecimal getSmallMoney(int index)`<br/><br/>`public BigDecimal getSmallMoney(String sCol)`|Ces méthodes sont ajoutées pour prendre en charge Always Encrypted pour les types de données Money, smallmoney, uniqueidentifier, DateTime et smalldatetime. <br/><br/>Notez que la méthode `setTimestamp()` existante est utilisée pour envoyer des valeurs de paramètre à la colonne datetime2 chiffrée. Pour les colonnes DateTime et smalldatetime chiffrées, utilisez les `setDateTime()` nouvelles `setSmallDateTime()` méthodes et, respectivement.|  
|`public void setObject(String parameterName, Object o, int n, int m, boolean forceEncrypt)`<br /><br /> `public void setObject(String parameterName, Object obj, SQLType jdbcType, int scale, boolean forceEncrypt)`<br /><br /> `public void setDate(String parameterName, java.sql.Date x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale, boolean forceEncrypt)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid, boolean forceEncrypt)`<br /><br /> `public void setBytes(String parameterName, byte[] b, boolean forceEncrypt)`<br /><br /> `public void setByte(String parameterName, byte b, boolean forceEncrypt)`<br /><br /> `public void setString(String parameterName, String s, boolean forceEncrypt)`<br /><br /> `public final void setNString(String parameterName, String value, boolean forceEncrypt)<br /><br /> public void setMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public void setDouble(String parameterName, double d, boolean forceEncrypt)`<br /><br /> `public void setFloat(String parameterName, float f, boolean forceEncrypt)`<br /><br /> `public void setInt(String parameterName, int i, boolean forceEncrypt)`<br /><br /> `public void setLong(String parameterName, long l, boolean forceEncrypt)`<br /><br /> `public void setShort(String parameterName, short s, boolean forceEncrypt)`<br /><br /> `public void setBoolean(String parameterNames, boolean b, boolean forceEncrypt)`<br/><br/>`public void setTimeStamp(String sCol, java.sql.Timestamp x, Calendar c, Boolean forceEncrypt)`|Définit le paramètre désigné sur la valeur Java donnée.<br /><br /> Si le forceEncrypt booléen a la valeur true, le paramètre de requête est défini uniquement si la colonne de désignation est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction.<br /><br /> Si le forceEncrypt booléen est défini sur false, le pilote ne force pas le chiffrement sur les paramètres.|
 

 Méthodes nouvelles ou surchargées dans la classe **SQLServerResultSet**  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public String getUniqueIdentifier(int columnIndex)`<br/><br/>`public String getUniqueIdentifier(String columnLabel)`<br/><br/>   `public java.sql.Timestamp getDateTime(int columnIndex)` <br/><br/> `public java.sql.Timestamp getDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getDateTime(int columnIndex, Calendar cal)`   <br/><br/>`public java.sql.Timestamp getDateTime(String colName, Calendar cal)`    <br/><br/>`public java.sql.Timestamp getSmallDateTime(int columnIndex)`    <br/><br/> `public java.sql.Timestamp getSmallDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(int columnIndex, Calendar cal)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(String colName, Calendar cal)`   <br/><br/>  `public BigDecimal getMoney(int columnIndex)`  <br/><br/> `public BigDecimal getMoney(String columnName)`   <br/><br/> `public BigDecimal getSmallMoney(int columnIndex)`   <br/><br/>  `public BigDecimal getSmallMoney(String columnName)`  <br/><br/>`public void updateMoney(String columnName, BigDecimal x)`    <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x)`  <br/><br/>     `public void updateDateTime(int index, java.sql.Timestamp x)` <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x)` |Ces méthodes sont ajoutées pour prendre en charge Always Encrypted pour les types de données Money, smallmoney, uniqueidentifier, DateTime et smalldatetime. <br/><br/>Notez que la méthode `updateTimestamp()` existante est utilisée pour la mise à jour des colonnes datetime2 chiffrées. Pour les colonnes DateTime et smalldatetime chiffrées, utilisez les `updateDateTime()` nouvelles `updateSmallDateTime()` méthodes et, respectivement.|
|`public void updateBoolean(int index, boolean x, boolean forceEncrypt)`  <br/><br/>  `public void updateByte(int index, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(int index, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(int index, int x, boolean forceEncrypt)`   <br/><br/>  `public void updateLong(int index, long x, boolean forceEncrypt)`  <br/><br/> `public void updateFloat(int index, float x, boolean forceEncrypt)`   <br/><br/> `public void updateDouble(int index, double x, boolean forceEncrypt)`   <br/><br/> `public void updateMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateSmallMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateBigDecimal(int index, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateString(int columnIndex, String stringValue, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(int columnIndex, String nString, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(String columnLabel, String nString, boolean forceEncrypt)`  <br/><br/> `public void updateBytes(int index, byte x[], boolean forceEncrypt)   <br/><br/>  public void updateDate(int index, java.sql.Date x, boolean forceEncrypt)`  <br/><br/> `public void updateTime(int index, java.sql.Time x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateTimestamp(int index, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/> `public void updateDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateUniqueIdentifier(int index, String x, boolean forceEncrypt)`    <br/><br/>  `public void updateObject(int index, Object x, int precision, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateObject(int index, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateBoolean(String columnName, boolean x, boolean forceEncrypt)`    <br/><br/>  `public void updateByte(String columnName, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(String columnName, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(String columnName, int x, boolean forceEncrypt)`   <br/><br/>   `public void updateLong(String columnName, long x, boolean forceEncrypt)` <br/><br/>  `public void updateFloat(String columnName, float x, boolean forceEncrypt)`  <br/><br/>  `public void updateDouble(String columnName, double x, boolean forceEncrypt)  <br/><br/> public void updateBigDecimal(String columnName, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateBigDecimal(String columnName, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateString(String columnName, String x, boolean forceEncrypt)`   <br/><br/>  `public void updateBytes(String columnName, byte x[], boolean forceEncrypt)`  <br/><br/> `public void updateDate(String columnName, java.sql.Date x, boolean forceEncrypt)`   <br/><br/>  `public void updateTime(String columnName, java.sql.Time x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateTimestamp(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateDateTimeOffset(String columnName, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateUniqueIdentifier(String columnName, String x, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object x, int precision, int scale, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`|Met à jour la colonne désignée avec la valeur Java donnée.<br/><br/>Si le forceEncrypt booléen a la valeur true, la colonne est définie uniquement si elle est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction.<br/><br/>Si le forceEncrypt booléen est défini sur false, le pilote ne force pas le chiffrement sur les paramètres.|

  
Nouveaux types dans la classe **Microsoft. Sql. types**

|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Utilisez ces types comme les types SQL cibles lors de l’envoi de **valeurs de** paramètre à des colonnes DateTime, smalldatetime, Money, smallmoney `setObject()/updateObject()` et uniqueidentifier chiffrées à l’aide de méthodes API.|  
  
  
 **Énumération SQLServerStatementColumnEncryptionSetting**  
  
 Spécifie la manière dont les données seront envoyées et reçues lors de la lecture et de l’écriture des colonnes chiffrées. En fonction de votre requête spécifique, vous pouvez réduire l’impact sur les performances en contournant le traitement du pilote Always Encrypted lorsque des colonnes non chiffrées sont utilisées. Notez que ces paramètres ne peuvent pas être utilisés pour contourner le chiffrement et accéder aux données en texte brut.  
  
 **Syntaxe**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Membres**  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|UseConnectionSetting|Spécifie que la commande doit avoir comme valeur par défaut le paramètre Always Encrypted dans la chaîne de connexion.|  
|Activé|Active Always Encrypted pour la requête.|  
|ResultSetOnly|Spécifie que seuls les résultats de la commande doivent être traités par la routine Always Encrypted dans le pilote. Utilisez cette valeur lorsque la commande n’a pas de paramètres nécessitant un chiffrement.|  
|Désactivé|Désactive Always Encrypted pour la requête.|  
  
 Le paramètre de niveau instruction pour AE est ajouté à la classe SQLServerConnection et à la classe SQLServerConnectionPoolProxy. Les méthodes suivantes de ces classes sont surchargées avec le nouveau paramètre.  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`public Statement createStatement(int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crée un objet d’instruction qui génère des objets ResultSet avec le type, la concurrence, la mise en attente et le paramètre de chiffrement de colonne donnés.|  
|`public CallableStatement prepareCall(String sql, int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)`|Crée un objet CallableStatement avec le paramètre de chiffrement de colonne donné qui génère des objets ResultSet avec le type, la concurrence et la fonctionnalité de mise en attente donnés.|  
|`public PreparedStatement prepareStatement(String sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donné qui a la capacité de récupérer des clés générées automatiquement.|  
|`public PreparedStatement prepareStatement(String sql, String[] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donné qui génère des objets ResultSet avec les noms de colonnes donnés.|  
|`public PreparedStatement prepareStatement(String sql, int[] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting`|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donné qui génère des objets ResultSet avec les index de colonne donnés.|  
|`public PreparedStatement prepareStatement(String sql, int nType, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donné qui génère des objets ResultSet avec le type, la concurrence et la fonctionnalité de mise en attente donnés.|  
  
> [!NOTE]  
>  Si Always Encrypted est désactivé pour une requête et que la requête a des paramètres qui doivent être chiffrés (paramètres qui correspondent à des colonnes chiffrées), la requête échoue.  
>   
>  Si Always Encrypted est désactivé pour une requête et que la requête retourne des résultats à partir de colonnes chiffrées, la requête retourne des valeurs chiffrées. Les valeurs chiffrées auront le type de données varbinary.  
  
 ## <a name="see-also"></a>Voir aussi  
 [Utilisation d'Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

