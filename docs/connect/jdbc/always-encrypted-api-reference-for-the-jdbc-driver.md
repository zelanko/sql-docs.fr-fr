---
title: Informations de référence sur l’API Always Encrypted pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1b720a607b702e93643d70b40a5e6ab036f2f56
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279250"
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
|Nouvelles méthodes :<br /><br /> public setColumnEncryptionTrustedMasterKeyPaths void statique (mappage < chaîne, liste\<chaîne >> trustedKeyPaths)<br /><br /> updateColumnEncryptionTrustedMasterKeyPaths de void statique public (serveur de la chaîne, liste\<chaîne > trustedKeyPaths)<br /><br /> public static void removeColumnEncryptionTrustedMasterKeyPaths (serveur de la chaîne)|Vous permet de définir/mettre à jour/supprimer une liste de chemins de clés approuvés pour un serveur de bases de données. Si pendant le traitement d’une requête d’application, le pilote reçoit un chemin de clé qui ne figure pas dans la liste, la requête échoue. Cette propriété fournit une protection supplémentaire contre les attaques de sécurité au cours desquelles un ordinateur SQL Server compromis envoie des chemins de clés factices, qui peuvent entraîner une fuite des informations d’identification du magasin de clés.|  
|Nouvelle méthode :<br /><br /> public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()|Retourne une liste de chemins d’accès de clés approuvés pour un serveur de bases de données.|  
|Nouvelle méthode :<br /><br /> public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)|Vous permet d’inscrire des fournisseurs de magasins de clés personnalisés. Il s’agit d’un dictionnaire qui mappe des noms de fournisseurs de magasins de clés à des implémentations de fournisseurs de magasins de clés.<br /><br /> Pour utiliser le magasin de clés JVM, vous devez instancier un objet SQLServerColumnEncryptionJVMKeyStoreProvider avec des informations d’identification du magasin de clés JVM et l’inscrire auprès du pilote. Le nom de ce fournisseur doit être « MSSQL_JVM_KEYSTORE ».<br /><br /> Pour utiliser le magasin de Azure Key Vault, vous devez instancier un objet SQLServerColumnEncryptionAzureKeyStoreProvider et l’inscrire auprès du pilote. Le nom de ce fournisseur doit être « AZURE_KEY_VAULT ».|
|public final boolean getSendTimeAsDatetime()|Retourne le paramètre de la propriété de connexion sendTimeAsDatetime.|
|setSendTimeAsDatetime void publique (sendTimeAsDateTimeValue booléenne)|Modifie le paramètre de la propriété de connexion sendTimeAsDatetime.|

 **Classe de SQLServerConnectionPoolProxy**
|Nom   |Description|  
|----------|-----------------|  
|public final boolean getSendTimeAsDatetime()|Retourne le paramètre de la propriété de connexion sendTimeAsDatetime.|
|setSendTimeAsDatetime void publique (sendTimeAsDateTimeValue booléenne)|Modifie le paramètre de la propriété de connexion sendTimeAsDatetime.|
     
  
 **SQLServerDataSource, classe**  
  
|Nom   |Description|  
|----------|-----------------|  
|public void setColumnEncryptionSetting(String columnEncryptionSetting)|Active/désactive la fonctionnalité Always Encrypted pour l’objet de source de données.<br /><br /> La valeur par défaut est Disabled.|  
|public getColumnEncryptionSetting() de chaîne|Récupère le paramètre de fonctionnalité Always Encrypted pour l’objet de source de données.|
|setKeyStoreAuthentication void publique (chaîne keyStoreAuthentication)|Définit le nom qui identifie un magasin de clés. Seule valeur prise en charge est la **JavaKeyStorePassword** pour identifier le Store de clé Java.<br/><br/>La valeur par défaut est null.|
|public getKeyStoreAuthentication() de chaîne|Obtient la valeur du paramètre keyStoreAuthentication pour l’objet de source de données.|
|setKeyStoreSecret void publique (chaîne keyStoreSecret)|Définit le mot de passe pour le magasin de clés Java. Le mot de passe pour le magasin de clés et la clé doit être identiques. Notez que keyStoreAuthentication doit être définie avec **JavaKeyStorePassword**.|
|setKeyStoreLocation void publique (chaîne keyStoreLocation)|Définit l’emplacement, y compris le nom de fichier pour le magasin de clés Java. Notez que keyStoreAuthentication doit être définie avec **JavaKeyStorePassword**.|
|public getKeyStoreLocation() de chaîne|Récupère la keyStoreLocation pour le Store de clé Java.|
  
 **Classe de SQLServerColumnEncryptionJavaKeyStoreProvider**  
  
 Implémentation du fournisseur de magasins de clés pour le magasin de clés Java. Cette classe permet d’utiliser des certificats stockés dans le magasin de clés Java comme clés principales de colonne.  
  
 Constructeurs  
  
|Nom   |Description|  
|----------|-----------------|  
|public SQLServerColumnEncryptionJavaKeyStoreProvider (chaîne keyStoreLocation, char [] keyStoreSecret)|Fournisseur de magasin de clés pour le Store de clé Java.|  
  
 Méthodes  
  
|Nom   |Description|  
|----------|-----------------|  
|public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)|Déchiffre la valeur chiffrée spécifiée d’une clé CEK. La valeur chiffrée est censée être chiffrée à l’aide du certificat avec le chemin d’accès de clé spécifié et à l’aide de l’algorithme spécifié.<br /><br /> **Le format du chemin de clé doit être un des suivants :**<br /><br /> Thumbprint:<empreinte_certificate><br /><br /> Alias:<alias_certificat><br /><br /> (Remplace SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (String, String, Byte[]).)|  
|public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)|Chiffre une clé CEK à l’aide du certificat avec le chemin d’accès de clé spécifié et à l’aide de l’algorithme spécifié.<br /><br /> **Le format du chemin de clé doit être un des suivants :**<br /><br /> Thumbprint:<empreinte_certificate><br /><br /> Alias:<alias_certificat><br /><br /> (Remplace SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (String, String, Byte[]).)|  
|setName void publique (nom de chaîne)|Définit le nom de ce fournisseur de magasin de clés.|
|public String getName ()|Obtient le nom de ce fournisseur de magasin de clés.|
  
 **Classe de SQLServerColumnEncryptionAzureKeyVaultProvider**  
  
 Implémentation du fournisseur de magasins de clés pour Azure Key Vault. Cette classe permet à l’aide des clés stockées dans Azure Key Vault en tant que clés principales de colonne.  
  
 Constructeurs  
  
|Nom   |Description|  
|----------|-----------------|  
|public SQLServerColumnEncryptionAzureKeyVaultProvider (clientId de chaîne, chaîne clientKey)|Fournisseur de magasin de clés pour Azure Key Vault.  Vous devez fournir l’identificateur et la clé du client demande le jeton pour s’authentifier auprès d’Azure Key Vault.|  
  
 Méthodes  
  
|Nom   |Description|  
|----------|-----------------|  
|public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)|Déchiffre la valeur chiffrée spécifiée d’une clé CEK. La valeur chiffrée doit être chiffrée avec la clé IDmaster de la clé de colonne spécifiée et avec l’algorithme spécifié. <br />(Remplace SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey (String, String, Byte[]).)|  
|public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)|Chiffre une clé de chiffrement de colonne à l’aide de la clé principale de colonne spécifiée et à l’aide de l’algorithme spécifié. <br />(Remplace SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey (String, String, Byte[]).)|  
|setName void publique (nom de chaîne)|Définit le nom de ce fournisseur de magasin de clés.|
|public String getName ()|Obtient le nom de ce fournisseur de magasin de clés.|  
  
  
 **Interface de SQLServerKeyVaultAuthenticationCallback**  
  
 Cette interface contient une méthode pour l’authentification Azure Key Vault, ce qui doit être implémentée par l’utilisateur.  
  
 Méthodes  
  
|Nom   |Description|  
|----------|-----------------|  
|getAccessToken de chaîne publique (autorité de chaîne, ressource de type chaîne, étendue de la chaîne) ;|La méthode doit être substituée. La méthode est utilisée pour obtenir un jeton à Azure Key Vault accès.|  
  
 **SQLServerColumnEncryptionKeyStoreProvider Class**  
  
 Étendez cette classe pour implémenter un fournisseur de magasins de clés personnalisé.  
  
|Nom   |Description|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Classe de base pour tous les fournisseurs de magasins de clés. Un fournisseur personnalisé doit dériver de cette classe et remplacer ses fonctions membres, puis l’inscrire avec SQLServerConnection. registerColumnEncryptionKeyStoreProviders().|  
  
 Méthodes  
  
|Nom   |Description|  
|----------|-----------------|  
|public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)|Méthode de classe de base pour déchiffrer la valeur chiffrée spécifiée d’une clé CEK. La valeur chiffrée doit être chiffrée en utilisant la clé principale de colonne avec le chemin de clé spécifié et l’algorithme spécifié.|  
|public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)|Méthode de classe de base pour chiffrer une clé CEK à l’aide de la clé CMK avec le chemin d’accès de clé spécifié et à l’aide de l’algorithme spécifié.|
|setName public void abstraite (nom de chaîne)|Définit le nom de ce fournisseur de magasin de clés.|
|public getName() chaîne abstraite|Obtient le nom de ce fournisseur de magasin de clés.|  
  
 Méthodes nouvelles ou surchargés dans **SQLServerPreparedStatement** classe  
  
|Nom   |Description|  
|----------|-----------------|  
|setBigDecimal void publique (int parameterIndex, BigDecimal x, int, précision, échelle d’int)<br /><br /> public setObject void (int parameterIndex, objet x, int targetSqlType, précision entier, à l’échelle d’int)<br /><br /> public setObject void (int parameterIndex, objet x, SQLType targetSqlType, précision entier, à l’échelle de l’entier)<br /><br /> public setTime void (parameterIndex d’int, java.sql.Time, int échelle x)<br /><br /> public setTimestamp void (parameterIndex d’int, java.sql.Timestamp, int échelle x) <br />public setDateTimeOffset void (int parameterIndex, microsoft.sql.DateTimeOffset x, mise à l’échelle d’int)|Ces méthodes sont surchargées avec une précision ou un argument d’échelle ou les deux pour prendre en charge d’Always Encrypted pour les types de données spécifiques qui nécessitent une précision et l’échelle d’informations.|  
|setMoney void publique (int parameterIndex, BigDecimal x)<br /><br /> setSmallMoney void publique (int parameterIndex, BigDecimal x)<br /><br /> public setUniqueIdentifier void (int parameterIndex, chaîne guid)<br /><br /> setDateTime void publique (parameterIndex int, java.sql.Timestamp x)<br /><br /> setSmallDateTime void publique (parameterIndex int, java.sql.Timestamp x)|Ces méthodes sont ajoutées pour prendre en charge d’Always Encrypted de types de données money, smallmoney, uniqueidentifier, datetime et smalldatetime. <br/><br/>Notez que la méthode setTimestamp() existant est utilisée pour envoyer des valeurs de paramètre dans la colonne chiffrée datetime2. Pour datetime chiffrée et colonnes smalldatetime utiliser les nouvelles méthodes setDateTime() setSmallDateTime() respectivement.|  
|setBigDecimal finale public void (int parameterIndex, BigDecimal x, int précision, échelle int, boolean forceEncrypt)<br /><br /> setMoney public void finale (int parameterIndex, BigDecimal x forceEncrypt booléenne)<br /><br /> setSmallMoney public void finale (int parameterIndex, BigDecimal x forceEncrypt booléenne)<br /><br /> setBoolean finale public void (int parameterIndex, x boolean, boolean forceEncrypt)<br /><br /> setByte finale public void (parameterIndex d’int, byte x forceEncrypt booléenne)<br /><br /> setBytes finale public void (int parameterIndex, octets x[], boolean forceEncrypt)<br /><br /> setUniqueIdentifier finale public void (int parameterIndex, chaîne guid, boolean forceEncrypt)<br /><br /> setDouble finale public void (parameterIndex d’int, double x, forceEncrypt booléenne)<br /><br /> setFloat finale public void (parameterIndex d’int, float x, forceEncrypt booléenne)<br /><br /> setInt finale public void (int parameterIndex, valeur int, boolean forceEncrypt)<br /><br /> setLong finale public void (parameterIndex d’int, long x, forceEncrypt booléenne)<br /><br /> public setObject finale (parameterIndex int, objet x, int targetSqlType, précision de l’entier, échelle int, boolean forceEncrypt)<br /><br /> setObject finale public void (int parameterIndex, objet x, SQLType targetSqlType, entier précision, entier échelle, boolean forceEncrypt)<br /><br /> setShort finale public void (parameterIndex d’int, short x, forceEncrypt booléenne)<br /><br /> setString public void finale (forceEncrypt booléenne parameterIndex, str String, int)<br /><br /> setNString finale public void (int parameterIndex, valeur de chaîne, booléen forceEncrypt)<br /><br /> publique setTime void finale (parameterIndex int, java.sql.Time x, mise à l’échelle d’int, boolean forceEncrypt)<br /><br /> public setTimestamp void finale (parameterIndex int, java.sql.Timestamp, int échelle x, forceEncrypt booléenne)<br /><br /> public setDateTimeOffset void finale (int parameterIndex, microsoft.sql.DateTimeOffset x, mise à l’échelle d’int, boolean forceEncrypt)<br /><br /> setDateTime finale public void (parameterIndex d’int, java.sql.Timestamp x forceEncrypt booléenne)<br /><br /> setSmallDateTime finale public void (parameterIndex d’int, java.sql.Timestamp x forceEncrypt booléenne)<br /><br /> public setDate void finale (parameterIndex int, java.sql.Date x java.util.Calendar cal, boolean forceEncrypt)<br /><br /> public setTime void finale (parameterIndex int, java.sql.Time x java.util.Calendar cal, boolean forceEncrypt)<br /><br /> public setTimestamp void finale (parameterIndex int, java.sql.Timestamp x java.util.Calendar cal, boolean forceEncrypt)|Définit le paramètre désigné sur la valeur Java donnée.<br /><br /> Si le forceEncrypt booléenne est définie sur true, la requête paramètre sera uniquement être défini si la désignation de colonne est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction.<br /><br /> Si le forceEncrypt booléenne est définie sur false, le pilote ne sont pas forcer le chiffrement sur les paramètres.|  
  
 Méthodes nouvelles ou surchargés dans **SQLServerCallableStatement** classe  
  
|Nom   |Description|  
|----------|-----------------|  
|public registerOutParameter void (parameterIndex d’int, int sqlType, précision de type int, int mise à l’échelle)<br /><br /> public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)<br /><br /> public registerOutParameter void (String parameterName, sqlType d’int, int précision, mise à l’échelle d’int)<br /><br /> public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)<br />public setBigDecimal void (String parameterName BigDecimal bd, précision de type int, int mise à l’échelle)<br /><br /> public setTime void (String parameterName, java.sql.Time t, mise à l’échelle d’int)<br /><br /> public setTimestamp void (String parameterName, t de java.sql.Timestamp, int mise à l’échelle)<br /><br /> public setDateTimeOffset void (String parameterName, microsoft.sql.DateTimeOffset t, mise à l’échelle d’int)<br/><br/>setObject finale public void (sCol de chaîne, objet x, int targetSqlType, précision entier, à l’échelle d’int)|Ces méthodes sont surchargées avec une précision ou un argument d’échelle ou les deux pour prendre en charge d’Always Encrypted pour les types de données spécifiques qui nécessitent une précision et l’échelle d’informations.|  
|setDateTime void publique (String parameterName, java.sql.Timestamp x)<br /><br /> setSmallDateTime void publique (String parameterName, java.sql.Timestamp x)<br /><br /> public setUniqueIdentifier void (nom_paramètre de chaîne, chaîne guid)<br /><br /> public setMoney void (String parameterName, BigDecimal bd)<br /><br /> public setSmallMoney void (String parameterName, BigDecimal bd)<br/><br/>public Timestamp getDateTime (int index)<br/><br/>public Timestamp getDateTime (chaîne sCol)<br/><br/>public getDateTime d’horodatage (int index, calendrier cal)<br/><br/>public getSmallDateTime Timestamp (int index)<br/><br/>public getSmallDateTime Timestamp (chaîne sCol)<br/><br/>public getSmallDateTime d’horodatage (int index, calendrier cal)<br/><br/>public getSmallDateTime d’horodatage (nom de la chaîne, calendrier cal)<br/><br/>public BigDecimal getMoney (int index)<br/><br/>public BigDecimal getMoney (chaîne sCol)<br/><br/>public BigDecimal getSmallMoney (int index)<br/><br/>public BigDecimal getSmallMoney (chaîne sCol)|Ces méthodes sont ajoutées pour prendre en charge d’Always Encrypted de types de données money, smallmoney, uniqueidentifier, datetime et smalldatetime. <br/><br/>Notez que la méthode setTimestamp() existant est utilisée pour envoyer des valeurs de paramètre dans la colonne chiffrée datetime2. Pour datetime chiffrée et colonnes smalldatetime utiliser les nouvelles méthodes setDateTime() setSmallDateTime() respectivement.|  
|public setObject void (String parameterName, Object o, int n, m d’int, boolean forceEncrypt)<br /><br /> public setObject void (String parameterName, objet obj, SQLType jdbcType, int mise à l’échelle, boolean forceEncrypt)<br /><br /> setDate void publique (String parameterName, java.sql.Date x c de calendrier, boolean forceEncrypt)<br /><br /> public setTime void (String parameterName, java.sql.Time t, int mise à l’échelle, boolean forceEncrypt)<br /><br /> setTime void publique (String parameterName, java.sql.Time x c de calendrier, boolean forceEncrypt)<br /><br /> public setDateTime void (String parameterName, java.sql.Timestamp x forceEncrypt booléenne)<br /><br /> public setDateTimeOffset void (String parameterName, microsoft.sql.DateTimeOffset t, int mise à l’échelle, boolean forceEncrypt)<br /><br /> public setSmallDateTime void (String parameterName, java.sql.Timestamp x forceEncrypt booléenne)<br /><br /> public setTimestamp void (String parameterName, t de java.sql.Timestamp, int mise à l’échelle, forceEncrypt booléenne)<br /><br /> public setTimestamp void (String parameterName, java.sql.Timestamp x forceEncrypt booléenne)<br /><br /> public setUniqueIdentifier void (nom_paramètre de chaîne, chaîne guid, boolean forceEncrypt)<br /><br /> public setBytes void (String parameterName, byte [] b, boolean forceEncrypt)<br /><br /> public setByte void (String parameterName, octet b, boolean forceEncrypt)<br /><br /> public setString void (String parameterName, de mappage de chaîne, booléen forceEncrypt)<br /><br /> setNString finale public void (String parameterName, valeur de chaîne, booléen forceEncrypt)<br /><br /> public setMoney void (String parameterName, BigDecimal bd, boolean forceEncrypt)<br /><br /> public setSmallMoney void (String parameterName, BigDecimal bd, boolean forceEncrypt)<br /><br /> public setBigDecimal void (String parameterName, BigDecimal bd, précision de type int, int mise à l’échelle, forceEncrypt booléenne)<br /><br /> public setDouble void (String parameterName, double d, boolean forceEncrypt)<br /><br /> public setFloat void (String parameterName, float f, boolean forceEncrypt)<br /><br /> setInt void publique (String parameterName, int i, boolean forceEncrypt)<br /><br /> public setLong void (String parameterName, long l, forceEncrypt booléenne)<br /><br /> public setShort void (String parameterName, short s, boolean forceEncrypt)<br /><br /> public setBoolean void (parameterNames de chaîne, valeur booléenne b, forceEncrypt booléenne)<br/><br/>setTimeStamp void publique (chaîne sCol, java.sql.Timestamp x c de calendrier, Boolean forceEncrypt)|Définit le paramètre désigné sur la valeur Java donnée.<br /><br /> Si le forceEncrypt booléenne est définie sur true, la requête paramètre sera uniquement être défini si la désignation de colonne est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction.<br /><br /> Si le forceEncrypt booléenne est définie sur false, le pilote ne sont pas forcer le chiffrement sur les paramètres.|
 

 Méthodes nouvelles ou surchargés dans **SQLServerResultSet** classe  
  
|Nom   |Description|  
|----------|-----------------|  
|getUniqueIdentifier chaîne publique (columnIndex int)<br/><br/>getUniqueIdentifier chaîne publique (chaîne columnLabel)<br/><br/>   java.sql.Timestamp publique getDateTime (columnIndex int) <br/><br/> java.sql.Timestamp publique getDateTime (columnName chaîne)   <br/><br/> java.sql.Timestamp publique getDateTime (int columnIndex, calendrier cal)   <br/><br/>java.sql.Timestamp publique getDateTime (chaîne colName, calendrier cal)    <br/><br/>java.sql.Timestamp publique getSmallDateTime (columnIndex int)    <br/><br/> java.sql.Timestamp publique getSmallDateTime (columnName chaîne)   <br/><br/> getSmallDateTime java.sql.Timestamp publique (int columnIndex, calendrier cal)   <br/><br/> getSmallDateTime java.sql.Timestamp publique (chaîne colName, calendrier cal)   <br/><br/>  public BigDecimal getMoney (columnIndex int)  <br/><br/> public BigDecimal getMoney (columnName chaîne)   <br/><br/> public BigDecimal getSmallMoney (columnIndex int)   <br/><br/>  public BigDecimal getSmallMoney (columnName chaîne)  <br/><br/>updateMoney void publique (chaîne columnName, BigDecimal x)    <br/><br/>  updateSmallMoney void publique (chaîne columnName, BigDecimal x)  <br/><br/>     updateDateTime void publique (index de type int, java.sql.Timestamp x) <br/><br/> updateSmallDateTime void publique (index de type int, java.sql.Timestamp x) |Ces méthodes sont ajoutées pour prendre en charge d’Always Encrypted pour types de données money, smallmoney, uniqueidentifier, datetime et smalldatetime. <br/><br/>Notez que la méthode updateTimestamp() existant est utilisée pour la mise à jour des colonnes datetime2 chiffré. Pour datetime chiffrée et colonnes smalldatetime utiliser les nouvelles méthodes updateDateTime() updateSmallDateTime() respectivement.|
|public updateBoolean void (int index, x boolean, boolean forceEncrypt)  <br/><br/>  public updateByte void (index de type int, byte x forceEncrypt booléenne)  <br/><br/>  public updateShort void (int index, x court, forceEncrypt booléenne)  <br/><br/> public updateInt void (index de type int, int x forceEncrypt booléenne)   <br/><br/>  public updateLong void (index de type int, long x, forceEncrypt booléenne)  <br/><br/> public updateFloat void (index de type int, float x, forceEncrypt booléenne)   <br/><br/> public updateDouble void (index de type int, double x, forceEncrypt booléenne)   <br/><br/> updateMoney void publique (int index, BigDecimal x forceEncrypt booléenne)   <br/><br/>  updateMoney void publique (chaîne columnName, BigDecimal x forceEncrypt booléenne)  <br/><br/> updateSmallMoney void publique (int index, BigDecimal x forceEncrypt booléenne)   <br/><br/>  updateSmallMoney void publique (chaîne columnName, BigDecimal x forceEncrypt booléenne)  <br/><br/> public updateBigDecimal void (int index, BigDecimal x, la précision de l’entier, à l’échelle de l’entier, booléen forceEncrypt)   <br/><br/>  public updateString void (int columnIndex, stringValue de chaîne, booléen forceEncrypt)  <br/><br/>  public updateNString void (int columnIndex, chaîne Nchaîne, boolean forceEncrypt)  <br/><br/>  public updateNString void (columnLabel de chaîne, chaîne Nchaîne, boolean forceEncrypt)  <br/><br/> public updateBytes void (int index, octets x[], boolean forceEncrypt)   <br/><br/>  public updateDate void (index de type int, java.sql.Date x forceEncrypt booléenne)  <br/><br/> updateTime void publique (index int, java.sql.Time, entier échelle x, forceEncrypt booléenne)   <br/><br/> updateTimestamp void publique (index int, java.sql.Timestamp, int échelle x, forceEncrypt booléenne)   <br/><br/> updateDateTime void publique (index int, java.sql.Timestamp, entier échelle x, forceEncrypt booléenne)   <br/><br/> updateSmallDateTime void publique (index int, java.sql.Timestamp, entier échelle x, forceEncrypt booléenne)   <br/><br/>  updateDateTimeOffset void publique (int index, microsoft.sql.DateTimeOffset x, à l’échelle de l’entier, booléen forceEncrypt)  <br/><br/> updateUniqueIdentifier void publique (int index, chaîne x forceEncrypt booléenne)    <br/><br/>  public updateObject void (int index, objet x, int précision, échelle int, boolean forceEncrypt)  <br/><br/>  publique updateObject void (int index, objet obj, SQLType targetSqlType, int mise à l’échelle, boolean forceEncrypt)  <br/><br/> public updateBoolean void (columnName de chaîne, booléen x, forceEncrypt booléenne)    <br/><br/>  public updateByte void (columnName de String, byte x forceEncrypt booléenne)  <br/><br/>  public updateShort void (chaîne columnName, x court, forceEncrypt booléenne)  <br/><br/> public updateInt void (columnName de chaîne, int x forceEncrypt booléenne)   <br/><br/>   public updateLong void (columnName de chaîne, long x, forceEncrypt booléenne) <br/><br/>  public updateFloat void (chaîne columnName, float x, forceEncrypt booléenne)  <br/><br/>  public updateDouble void (columnName de chaîne, double x, forceEncrypt booléenne)  <br/><br/> updateBigDecimal void publique (chaîne columnName, BigDecimal x forceEncrypt booléenne)   <br/><br/>  public updateBigDecimal void (chaîne columnName, BigDecimal x, la précision de l’entier, à l’échelle de l’entier, booléen forceEncrypt)  <br/><br/> updateString void publique (columnName de chaîne, chaîne x forceEncrypt booléenne)   <br/><br/>  public updateBytes void (chaîne columnName, octets x[], boolean forceEncrypt)  <br/><br/> public updateDate void (chaîne columnName, java.sql.Date x forceEncrypt booléenne)   <br/><br/>  updateTime void publique (chaîne columnName, java.sql.Time x, mise à l’échelle d’int, boolean forceEncrypt)  <br/><br/>  updateTimestamp void publique (chaîne columnName, java.sql.Timestamp, int échelle x, forceEncrypt booléenne)  <br/><br/> updateDateTime void publique (chaîne columnName, java.sql.Timestamp, int échelle x, forceEncrypt booléenne)   <br/><br/>  updateSmallDateTime void publique (chaîne columnName, java.sql.Timestamp, int échelle x, forceEncrypt booléenne)  <br/><br/>  updateDateTimeOffset void publique (chaîne columnName, microsoft.sql.DateTimeOffset x, mise à l’échelle d’int, boolean forceEncrypt)  <br/><br/>  updateUniqueIdentifier void publique (columnName de chaîne, chaîne x forceEncrypt booléenne)<br/><br/>public updateObject void (columnName de chaîne, objet x, int précision, échelle int, boolean forceEncrypt)<br/><br/>public updateObject void (columnName de chaîne, objet obj, SQLType targetSqlType, int mise à l’échelle, boolean forceEncrypt)|Mettre à jour la colonne désignée à la valeur java donnée.<br/><br/>Si le forceEncrypt booléenne est définie sur true, la colonne n’a la valeur si elle est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction.<br/><br/>Si le forceEncrypt booléenne est définie sur false, le pilote ne sont pas forcer le chiffrement sur les paramètres.|

  
Nouveaux types dans **microsoft.sql.Types** classe
|Nom   |Description|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Utiliser ces types en tant que types SQL cibles lors de l’envoi des valeurs de paramètre à **chiffrées** datetime, smalldatetime, money, smallmoney, les colonnes uniqueidentifier à l’aide de méthodes de setObject()/updateObject() API.|  
  
  
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
|createStatement d’instruction publique (%nLes d’int, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crée un objet d’instruction qui génère des objets de jeu de résultats avec le type donné, d’accès concurrentiel, mise en attente et paramètre de chiffrement de colonne.|  
|prepareCall de CallableStatement publique (chaîne sql, %nLes d’int, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)|Crée un objet de CallableStatement avec le paramètre de chiffrement de colonne donné qui génère des objets de jeu de résultats avec le type donné, d’accès concurrentiel et mise en attente.|  
|prepareStatement de PreparedStatement publique (chaîne sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donné qui a la possibilité de récupérer les clés générées automatiquement.|  
|prepareStatement de PreparedStatement publique (sql de la chaîne, chaîne [] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donnée qui génère des objets de jeu de résultats avec les noms de colonne donnée.|  
|prepareStatement de PreparedStatement publique (chaîne sql, int [] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donnée qui génère des objets de jeu de résultats avec les index de colonne donné.|  
|prepareStatement de PreparedStatement publique (chaîne sql, %nLes d’int, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)|Crée un objet PreparedStatement avec le paramètre de chiffrement de colonne donné qui génère des objets de jeu de résultats avec le type donné, d’accès concurrentiel et mise en attente.|  
  
> [!NOTE]  
>  Si Always Encrypted est désactivé pour une requête et la requête avec des paramètres qui doivent être chiffrées (les paramètres qui correspondent aux colonnes chiffrées), la requête échoue.  
>   
>  Si Always Encrypted est désactivé pour une requête et la requête retourne des résultats à partir des colonnes chiffrées, la requête retournera les valeurs chiffrées. Les valeurs chiffrées aura le type de données varbinary.  
  
 ## <a name="see-also"></a> Voir aussi  
 [Utilisation du chiffrement intégral avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

