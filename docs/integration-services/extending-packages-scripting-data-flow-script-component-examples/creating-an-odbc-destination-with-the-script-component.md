---
title: "Création d’une Destination ODBC avec le composant de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5eb539f0d18f473b10ed8d49bcee9c298292fb41
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-odbc-destination-with-the-script-component"></a>Création d'une destination ODBC à l'aide du composant Script
  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous enregistrez en général des données vers une destination ODBC à l’aide un [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination et le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] du fournisseur de données pour ODBC. Toutefois, vous pouvez également créer une destination ODBC ad hoc à utiliser dans un package unique. Pour créer cette destination ODBC ad hoc, vous utilisez le composant Script comme indiqué dans l'exemple suivant.  
  
> [!NOTE]  
>  Si vous souhaitez créer un composant que vous pouvez réutiliser plus facilement dans plusieurs tâches de flux de données et plusieurs packages, utilisez le code présenté dans cet exemple de composant Script comme point de départ pour un composant de flux de données personnalisé. Pour plus d’informations, consultez [Développement d’un composant de flux de données personnalisé](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer un composant de destination qui utilise une version ODBC Gestionnaire de connexions pour enregistrer les données du flux de données dans un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.  
  
 Cet exemple est une version modifiée du personnalisé [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination qui a été présentée dans la rubrique, [création d’une Destination avec le composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Toutefois, dans cet exemple, la destination [!INCLUDE[vstecado](../../includes/vstecado-md.md)] personnalisée a été modifiée afin d'utiliser un gestionnaire de connexions ODBC et d'enregistrer les données dans une destination ODBC. Ces modifications incluent également les points suivants :  
  
-   Vous ne pouvez pas appeler la **AcquireConnection** méthode du Gestionnaire de connexions ODBC à partir du code managé, parce qu’elle retourne un objet natif. Par conséquent, cet exemple utilise la chaîne de connexion du gestionnaire de connexions pour se connecter directement à la source de données en utilisant le fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour ODBC managé.  
  
-   Le **OdbcCommand** attend des paramètres positionnels. Les positions des paramètres sont indiquées par les points d'interrogation (?) dans le texte de la commande. (En revanche, un **SqlCommand** attend des paramètres nommés.)  
  
 Cet exemple utilise le **Person.Address** de table dans le **AdventureWorks** base de données exemple. L’exemple passe les première et quatrième colonnes, le * *int*AddressID*** et **nvarchar (30) Ville** les colonnes de cette table via le flux de données. Ces mêmes données sont utilisées dans la source, transformation et des exemples de destination dans la rubrique [développement des Types de composants Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Pour configurer cet exemple de composant Script  
  
1.  Créer une connexion ODBC manager se connecte à la **AdventureWorks** base de données.  
  
2.  Créer une table de destination en exécutant la commande Transact-SQL suivante dans le **AdventureWorks** base de données :  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que destination.  
  
4.  Connectez la sortie d'une source ou transformation en amont au composant de destination dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Vous pouvez connecter directement une source à une destination sans transformation.) Pour vous assurer que cet exemple fonctionne, la sortie du composant en amont doit inclure au moins les **AddressID** et **Ville** colonnes à partir de la **Person.Address** table de la **AdventureWorks** base de données exemple.  
  
5.  Ouvrez l' **Éditeur de transformation de script**. Sur le **colonnes d’entrée** page, sélectionnez le **AddressID** et **Ville** colonnes.  
  
6.  Sur le **entrées et sorties** page, renommez l’entrée avec un nom plus descriptif tel que **MyAddressInput**.  
  
7.  Sur le **gestionnaires de connexions** page, ajoutez ou créez la connexion ODBC Gestionnaire avec un nom descriptif tel que **MyODBCConnectionManager**.  
  
8.  Sur le **Script** , cliquez sur **modifier le Script**, puis entrez le script ci-dessous dans le **ScriptMain** classe.  
  
9. Fermez l’environnement de développement script, fermez le **éditeur de Transformation de Script**, puis exécutez l’exemple.  
  
    ```vb  
    Imports System.Data.Odbc  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim odbcConn As OdbcConnection  
        Dim odbcCmd As OdbcCommand  
        Dim odbcParam As OdbcParameter  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connectionString As String  
            connectionString = Me.Connections.MyODBCConnectionManager.ConnectionString  
            odbcConn = New OdbcConnection(connectionString)  
            odbcConn.Open()  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            odbcCmd = New OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
                "VALUES(?, ?)", odbcConn)  
            odbcParam = New OdbcParameter("@addressid", OdbcType.Int)  
            odbcCmd.Parameters.Add(odbcParam)  
            odbcParam = New OdbcParameter("@city", OdbcType.NVarChar, 30)  
            odbcCmd.Parameters.Add(odbcParam)  
  
        End Sub  
  
        Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
            With odbcCmd  
                .Parameters("@addressid").Value = Row.AddressID  
                .Parameters("@city").Value = Row.City  
                .ExecuteNonQuery()  
            End With  
  
        End Sub  
  
        Public Overrides Sub ReleaseConnections()  
  
            odbcConn.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.Data.Odbc;  
    ...  
    public class ScriptMain :  
        UserComponent  
    {  
        OdbcConnection odbcConn;  
        OdbcCommand odbcCmd;  
        OdbcParameter odbcParam;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            string connectionString;  
            connectionString = this.Connections.MyODBCConnectionManager.ConnectionString;  
            odbcConn = new OdbcConnection(connectionString);  
            odbcConn.Open();  
  
        }  
  
        public override void PreExecute()  
        {  
  
            odbcCmd = new OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " +  
                "VALUES(?, ?)", odbcConn);  
            odbcParam = new OdbcParameter("@addressid", OdbcType.Int);  
            odbcCmd.Parameters.Add(odbcParam);  
            odbcParam = new OdbcParameter("@city", OdbcType.NVarChar, 30);  
            odbcCmd.Parameters.Add(odbcParam);  
  
        }  
  
        public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
        {  
  
            {  
                odbcCmd.Parameters["@addressid"].Value = Row.AddressID;  
                odbcCmd.Parameters["@city"].Value = Row.City;  
                odbcCmd.ExecuteNonQuery();  
            }  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            odbcConn.Close();  
  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une destination à l’aide du composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
