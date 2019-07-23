---
title: Fonctionnement des transactions XA | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 574e326f-0520-4003-bdf1-62d92c3db457
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7caa67e019ce60f955abf60d215b6c049f3dc708
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004156"
---
# <a name="understanding-xa-transactions"></a>Présentation des transactions XA

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge les transactions distribuées facultatives Java Platform, Enterprise Edition/JDBC 2.0. Les connexions JDBC obtenues à partir de la classe [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) peuvent participer aux environnements de traitement des transactions distribuées standard, tels que les serveurs d’applications Java Platform, Enterprise Edition (Java EE).  

> [!WARNING]  
> Microsoft JDBC Driver 4.2 pour SQL (et versions ultérieures) inclut de nouvelles options de délai d’attente pour la fonctionnalité existante de restauration automatique des transactions non préparées. Pour plus d’informations, consultez [Configuration des paramètres de délai d’attente côté serveur pour la restauration automatique des transactions](../../connect/jdbc/understanding-xa-transactions.md#BKMK_ServerSide) non préparées plus loin dans cette rubrique.  

## <a name="remarks"></a>Notes

Les classes pour l'implémentation des transactions distribuées sont les suivantes :  
  
| Classe                                              | Implémentations                      | Description                                       |
| -------------------------------------------------- | ------------------------------- | ------------------------------------------------- |
| com.microsoft.sqlserver.jdbc.SQLServerXADataSource | javax.sql.XADataSource          | Fabrique de classe pour les connexions distribuées.    |
| com.microsoft.sqlserver.jdbc.SQLServerXAResource   | javax.transaction.xa.XAResource | Adaptateur de ressources pour le gestionnaire de transactions. |
  
> [!NOTE]  
> Les connexions de transactions distribuées XA sont définies par défaut au niveau d'isolation Read Committed.  
  
## <a name="guidelines-and-limitations-when-using-xa-transactions"></a>Recommandations et limitations relatives à l'utilisation de transactions XA  

Les recommandations supplémentaires suivantes s'appliquent aux transactions fortement couplées :  

- Lorsque vous utilisez des transactions XA avec Microsoft Distributed Transaction Coordinator (MS DTC), vous pouvez remarquer que la version actuelle de MS DTC ne prend pas en charge le comportement de branche XA fortement couplée. Par exemple, MS DTC a un mappage un-à-un entre un ID de transaction de branche XA (XID) et un ID de transaction MS DTC et le travail effectué par les branches XA couplées de manière lâche est isolé.  
  
     Le correctif logiciel disponible sur la page web [MSDTC et transactions fortement couplées](https://support.microsoft.com/kb/938653) permet la prise en charge des branches XA fortement couplées quand plusieurs branches XA avec le même ID de transaction globale (GTRID) sont mappées à un ID de transaction MS DTC unique. Cette prise en charge permet à plusieurs branches XA fortement couplées de voir les changements apportés à chacune d’elles dans le gestionnaire de ressources, par exemple [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
- Un indicateur [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) permet aux applications d’utiliser les transactions XA fortement couplées qui ont des ID de transaction de branche XA (BQUAL) différents mais le même ID de transaction global (GTRID) et ID de format (FormatID). Pour pouvoir utiliser cette fonctionnalité, vous devez définir [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) sur le paramètre flags de la méthode XAResource. Start:
  
    ```java
    xaRes.start(xid, SQLServerXAResource.SSTRANSTIGHTLYCPLD);  
    ```  
  
## <a name="configuration-instructions"></a>Instructions relatives à la configuration

Les étapes suivantes sont requises si vous souhaitez utiliser des sources de données XA avec Microsoft Distributed Transaction Coordinator (MS DTC) pour manipuler des transactions distribuées.  

> [!NOTE]  
> Les composants de transaction distribuée JDBC sont inclus dans le répertoire xa de l'installation du pilote JDBC. Ces composants incluent les fichiers xa_install.sql et sqljdbc_xa.dll.  

> [!NOTE]  
> À compter de SQL Server 2019 public Preview CTP 2,0, les composants JDBC de transaction distribuée JDBC sont inclus dans le moteur de SQL Server et peuvent être activés ou désactivés avec une procédure stockée système.
> Pour permettre aux composants requis d’effectuer des transactions distribuées XA à l’aide du pilote JDBC, exécutez la procédure stockée suivante.
>
> EXEC sp_sqljdbc_xa_install
>
> Pour désactiver les composants précédemment installés, exécutez la procédure stockée suivante.
>
> EXEC sp_sqljdbc_xa_uninstall

### <a name="running-the-ms-dtc-service"></a>Exécution du service MS DTC

Le service MS DTC doit être marqué comme **Automatique** dans Service Manager afin de garantir son exécution quand le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre. Pour activer MS DTC pour les transactions XA, vous devez procéder comme suit :  
  
Sur Windows Vista et versions ultérieures :  
  
1. Cliquez sur le bouton **Démarrer**, tapez **dcomcnfg** dans la zone **Rechercher**, puis appuyez sur Entrée pour ouvrir **Services de composants**. Vous pouvez également taper %windir%\system32\comexp.msc dans la zone **Rechercher** du menu Démarrer pour ouvrir **Services de composants**.  
  
2. Développez Services de composants, Ordinateurs, Poste de travail, puis Distributed Transaction Coordinator.  
  
3. Cliquez avec le bouton droit sur **DTC local**, puis sélectionnez **Propriétés**.  
  
4. Dans la boîte de dialogue **Propriétés du DTC local**, cliquez sur l’onglet **Sécurité**.  
  
5. Cochez la case **Activer les transactions XA**, puis cliquez sur **OK**. Cela entraîne le redémarrage du service MS DTC.
  
6. Cliquez à nouveau sur **OK** pour fermer la boîte de dialogue **Propriétés**, puis fermez **Services de composants**.  
  
7. Arrêtez, puis redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de garantir sa synchronisation avec les modifications de MS DTC.  

### <a name="configuring-the-jdbc-distributed-transaction-components"></a>Configuration des composants de transaction distribuée JDBC  

Vous pouvez configurer les composants de transaction distribuée du pilote JDBC en suivant les étapes suivantes :  
  
1. Copiez le nouveau fichier sqljdbc_xa.dll à partir du répertoire d’installation du pilote JDBC vers le répertoire Binn de chaque ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] susceptible de participer à des transactions distribuées.  
  
    > [!NOTE]  
    > Si vous utilisez des transactions XA avec un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 32 bits, utilisez le fichier sqljdbc_xa.dll dans le dossier x86, même si le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé sur un processeur x64. Si vous utilisez des transactions XA avec une version 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un processeur x64, utilisez le fichier sqljdbc_xa.dll dans le dossier x64.  
  
2. Exécutez le script de base de données xa_install.sql sur chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] susceptible de participer à des transactions distribuées. Ce script installe les procédures stockées étendues qui sont appelées par sqljdbc_xa.dll. Ces procédures stockées étendues implémentent la prise en charge des transactions distribuées et de XA pour [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]. Vous devez exécuter ce script en tant qu’administrateur de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3. Pour autoriser un utilisateur spécifique à participer à des transactions distribuées avec le pilote JDBC, ajoutez-le au rôle SqlJDBCXAUser.  
  
Vous ne pouvez configurer qu’une seule version à la fois de l’assembly sqljdbc_xa.dll sur chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les applications devront peut-être utiliser des versions différentes du pilote JDBC pour se connecter à la même instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais de la connexion XA. Dans ce cas, sqljdbc_xa.dll, qui est livré avec le pilote JDBC le plus récent, doit être installé sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Il existe trois façons de vérifier la version actuellement installée de sqljdbc_xa.dll sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :
  
1. Ouvrez le répertoire LOG de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui doit participer aux transactions distribuées. Sélectionnez et ouvrez le fichier ERRORLOG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Recherchez l'expression « Using 'SQLJDBC_XA.dll' version ... » dans le fichier ERRORLOG.  
  
2. Ouvrez le répertoire Binn de l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui doit participer aux transactions distribuées. Sélectionnez l’assembly sqljdbc_xa. dll.

    - Sur Windows Vista et versions ultérieures : cliquez avec le bouton droit sur sqljdbc_xa.dll, puis sélectionnez Propriétés. Cliquez ensuite sur l’onglet **Détails**. Le champ **Version du fichier** indique la version de sqljdbc_xa.dll actuellement installée sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3. Définissez la fonctionnalité de journalisation comme indiqué dans l'exemple de code de la prochaine section. Recherchez l'expression « Server XA DLL version:... » dans le fichier journal de sortie.  

### <a name="BKMK_ServerSide"></a> Configuration des paramètres du délai d’attente côté serveur pour la restauration automatique des transactions non préparées  

> [!WARNING]  
> Il s’agit d’une nouvelle option côté serveur proposée par Microsoft JDBC Driver 4.2 (et versions ultérieures) pour SQL Server. Pour obtenir le comportement mis à jour, assurez-vous que le fichier sqljdbc_xa.dll est mis à jour sur le serveur. Pour plus d’informations sur la définition des délais d’expiration côté client, voir [XAResource.setTransactionTimeout()](https://docs.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html).  

Il existe deux paramètres du Registre (valeurs DWORD) pour contrôler le comportement du délai d'attente des transactions distribuées :  
  
- **XADefaultTimeout** (en secondes): valeur de délai d’attente par défaut à utiliser lorsque l’utilisateur ne spécifie pas de délai d’attente. La valeur par défaut est 0.  
  
- **XAMaxTimeout** (en secondes): valeur maximale du délai d’attente qu’un utilisateur peut définir. La valeur par défaut est 0.  
  
Ces paramètres sont spécifiques de l'instance SQL Server et doivent être créés sous la clé de Registre suivante :  

```bash
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL<version>.<instance_name>\XATimeout  
```

> [!NOTE]  
> Pour un serveur SQL Server 32 bits exécuté sur des ordinateurs 64 bits, les paramètres de Registre doivent être créés sous la clé suivante : `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Microsoft SQL Server\MSSQL<version>.<instance_name>\XATimeout`
  
Une valeur de délai d'expiration est définie au démarrage de chaque transaction ; une fois ce délai écoulé, la transaction est restaurée par le serveur SQL Server. Le délai d'attente est déterminé en fonction de ces paramètres de Registre et de ce que l'utilisateur a spécifié via XAResource.setTransactionTimeout(). Voici quelques exemples d'interprétation des valeurs de délai d'attente :  
  
- `XADefaultTimeout = 0`, `XAMaxTimeout = 0`
  
     Signifie qu'aucun délai d'attente par défaut ne sera utilisé et qu'aucun délai d'attente maximal ne sera appliqué sur les clients. Dans ce cas, les transactions auront un délai d'attente uniquement si le client en définit un à l'aide de XAResource.setTransactionTimeout.  
  
- `XADefaultTimeout = 60`, `XAMaxTimeout = 0`
  
     Signifie que toutes les transactions auront un délai d'attente de 60 secondes si le client n'en spécifie aucun. Si le client spécifie un délai d'attente, cette valeur sera alors utilisée. Aucune valeur de délai d'attente maximale n'est appliquée.  
  
- `XADefaultTimeout = 30`, `XAMaxTimeout = 60`
  
     Signifie que toutes les transactions auront un délai d'attente de 30 secondes si le client n'en spécifie aucun. Si le client spécifie un délai d’attente, ce dernier sera utilisé s’il est inférieur à 60 secondes (valeur maximale).  
  
- `XADefaultTimeout = 0`, `XAMaxTimeout = 30`
  
     Signifie que toutes les transactions auront un délai d'attente de 30 secondes (valeur maximale) si le client n'en spécifie aucun. Si le client spécifie un délai d’attente, ce dernier sera utilisé s’il est inférieur à 30 secondes (valeur maximale).  
  
### <a name="upgrading-sqljdbcxadll"></a>Mise à niveau du fichier sqljdbc_xa.dll

Lorsque vous installez une nouvelle version du pilote JDBC, vous devez utiliser le fichier sqljdbc_xa.dll de la nouvelle version pour mettre à niveau le fichier sqljdbc_xa.dll sur le serveur.  
  
> [!IMPORTANT]  
> Vous devez mettre à niveau le fichier sqljdbc_xa.dll dans une fenêtre de maintenance ou quand aucune transaction MS DTC n’est en cours.
  
1. Déchargez sqljdbc_xa. dll [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de la commande **DBCC sqljdbc_xa (Free)** .  
  
2. Copiez le nouveau fichier sqljdbc_xa.dll à partir du répertoire d’installation du pilote JDBC vers le répertoire Binn de chaque ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] susceptible de participer à des transactions distribuées.  
  
    La nouvelle DLL sera chargée à l'appel d'une procédure étendue dans sqljdbc_xa.dll. Il n’est pas nécessaire de redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour charger les nouvelles définitions.  
  
### <a name="configuring-the-user-defined-roles"></a>Configuration des rôles définis par l'utilisateur

Pour autoriser un utilisateur spécifique à participer à des transactions distribuées avec le pilote JDBC, ajoutez-le au rôle SqlJDBCXAUser. Par exemple, utilisez le code [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant pour ajouter un utilisateur appelé « shelby » (« shelby » est un nom d’utilisateur standard d’ouverture de session SQL) au rôle SqlJDBCXAUser :  

```sql
USE master  
GO  
EXEC sp_grantdbaccess 'shelby', 'shelby'  
GO  
EXEC sp_addrolemember [SqlJDBCXAUser], 'shelby'  
```

Les rôles définis par l'utilisateur SQL sont définis par base de données. Pour des raisons de sécurité, si vous souhaitez créer votre propre rôle, vous devrez le définir dans chaque base de données et ajouter les utilisateurs base de données par base de données. Le rôle SqlJDBCXAUser est strictement défini dans la base de données MASTER, car il est utilisé pour accorder l'accès aux procédures stockées étendues SQL JDBC s’y trouvant. Vous devrez d'abord accorder à l'utilisateur un accès à la base de données MASTER, puis un accès au rôle SqlJDBCXAUser en étant connecté à la base de données MASTER.  

## <a name="example"></a>Exemple  

```java
import java.net.Inet4Address;
import java.sql.*;
import java.util.Random;
import javax.sql.XAConnection;
import javax.transaction.xa.*;
import com.microsoft.sqlserver.jdbc.*;


public class testXA {

    public static void main(String[] args) throws Exception {

        // Create variables for the connection string.
        String prefix = "jdbc:sqlserver://";
        String serverName = "localhost";
        int portNumber = 1433;
        String databaseName = "AdventureWorks";
        String user = "UserName";
        String password = "*****";

        String connectionUrl = prefix + serverName + ":" + portNumber + ";databaseName=" + databaseName + ";user="
                + user + ";password=" + password;

        Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement()) {
            stmt.executeUpdate("CREATE TABLE XAMin (f1 int, f2 varchar(max))");

        }
        // Create the XA data source and XA ready connection.
        SQLServerXADataSource ds = new SQLServerXADataSource();
        ds.setUser(user);
        ds.setPassword(password);
        ds.setServerName(serverName);
        ds.setPortNumber(portNumber);
        ds.setDatabaseName(databaseName);

        XAConnection xaCon = ds.getXAConnection();
        try (Connection con = xaCon.getConnection()) {

            // Get a unique Xid object for testing.
            XAResource xaRes = null;
            Xid xid = null;
            xid = XidImpl.getUniqueXid(1);

            // Get the XAResource object and set the timeout value.
            xaRes = xaCon.getXAResource();
            xaRes.setTransactionTimeout(0);

            // Perform the XA transaction.
            System.out.println("Write -> xid = " + xid.toString());
            xaRes.start(xid, XAResource.TMNOFLAGS);
            PreparedStatement pstmt = con.prepareStatement("INSERT INTO XAMin (f1,f2) VALUES (?, ?)");
            pstmt.setInt(1, 1);
            pstmt.setString(2, xid.toString());
            pstmt.executeUpdate();

            // Commit the transaction.
            xaRes.end(xid, XAResource.TMSUCCESS);
            xaRes.commit(xid, true);
        }
        xaCon.close();

        // Open a new connection and read back the record to verify that it worked.
        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT * FROM XAMin")) {
            rs.next();
            System.out.println("Read -> xid = " + rs.getString(2));
            stmt.executeUpdate("DROP TABLE XAMin");
        }
    }
}


class XidImpl implements Xid {

    public int formatId;
    public byte[] gtrid;
    public byte[] bqual;

    public byte[] getGlobalTransactionId() {
        return gtrid;
    }

    public byte[] getBranchQualifier() {
        return bqual;
    }

    public int getFormatId() {
        return formatId;
    }

    XidImpl(int formatId, byte[] gtrid, byte[] bqual) {
        this.formatId = formatId;
        this.gtrid = gtrid;
        this.bqual = bqual;
    }

    public String toString() {
        int hexVal;
        StringBuffer sb = new StringBuffer(512);
        sb.append("formatId=" + formatId);
        sb.append(" gtrid(" + gtrid.length + ")={0x");
        for (int i = 0; i < gtrid.length; i++) {
            hexVal = gtrid[i] & 0xFF;
            if (hexVal < 0x10)
                sb.append("0" + Integer.toHexString(gtrid[i] & 0xFF));
            else
                sb.append(Integer.toHexString(gtrid[i] & 0xFF));
        }
        sb.append("} bqual(" + bqual.length + ")={0x");
        for (int i = 0; i < bqual.length; i++) {
            hexVal = bqual[i] & 0xFF;
            if (hexVal < 0x10)
                sb.append("0" + Integer.toHexString(bqual[i] & 0xFF));
            else
                sb.append(Integer.toHexString(bqual[i] & 0xFF));
        }
        sb.append("}");
        return sb.toString();
    }

    // Returns a globally unique transaction id.
    static byte[] localIP = null;
    static int txnUniqueID = 0;

    static Xid getUniqueXid(int tid) {

        Random rnd = new Random(System.currentTimeMillis());
        txnUniqueID++;
        int txnUID = txnUniqueID;
        int tidID = tid;
        int randID = rnd.nextInt();
        byte[] gtrid = new byte[64];
        byte[] bqual = new byte[64];
        if (null == localIP) {
            try {
                localIP = Inet4Address.getLocalHost().getAddress();
            } catch (Exception ex) {
                localIP = new byte[] {0x01, 0x02, 0x03, 0x04};
            }
        }
        System.arraycopy(localIP, 0, gtrid, 0, 4);
        System.arraycopy(localIP, 0, bqual, 0, 4);

        // Bytes 4 -> 7 - unique transaction id.
        // Bytes 8 ->11 - thread id.
        // Bytes 12->15 - random number generated by using seed from current time in milliseconds.
        for (int i = 0; i <= 3; i++) {
            gtrid[i + 4] = (byte) (txnUID % 0x100);
            bqual[i + 4] = (byte) (txnUID % 0x100);
            txnUID >>= 8;
            gtrid[i + 8] = (byte) (tidID % 0x100);
            bqual[i + 8] = (byte) (tidID % 0x100);
            tidID >>= 8;
            gtrid[i + 12] = (byte) (randID % 0x100);
            bqual[i + 12] = (byte) (randID % 0x100);
            randID >>= 8;
        }
        return new XidImpl(0x1234, gtrid, bqual);
    }
}

```

## <a name="see-also"></a>Voir aussi  

[Réalisation de transactions avec le pilote JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
