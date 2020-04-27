---
title: Création d’une destination ODBC à l’aide du composant Script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5ac76e77d1bd5eebd2e796a6a72463564cb3df3c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62896185"
---
# <a name="creating-an-odbc-destination-with-the-script-component"></a>Création d'une destination ODBC à l'aide du composant Script
  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous enregistrez généralement les données dans une destination ODBC en utilisant une destination [!INCLUDE[vstecado](../../includes/vstecado-md.md)] et le fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour ODBC. Toutefois, vous pouvez également créer une destination ODBC ad hoc à utiliser dans un package unique. Pour créer cette destination ODBC ad hoc, vous utilisez le composant Script comme indiqué dans l'exemple suivant.  
  
> [!NOTE]  
>  Si vous souhaitez créer un composant que vous pouvez réutiliser plus facilement dans plusieurs tâches de flux de données et plusieurs packages, utilisez le code présenté dans cet exemple de composant Script comme point de départ pour un composant de flux de données personnalisé. Pour plus d’informations, consultez [Développement d’un composant de flux de données personnalisé](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer un composant de destination qui utilise un gestionnaire de connexions ODBC existant pour enregistrer des données du flux de données dans une table [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Cet exemple est une version modifiée de la destination [!INCLUDE[vstecado](../../includes/vstecado-md.md)] personnalisée présentée dans la rubrique [Création d’une destination à l’aide du composant Script](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Toutefois, dans cet exemple, la destination [!INCLUDE[vstecado](../../includes/vstecado-md.md)] personnalisée a été modifiée afin d'utiliser un gestionnaire de connexions ODBC et d'enregistrer les données dans une destination ODBC. Ces modifications incluent également les points suivants :  
  
-   Vous ne pouvez pas appeler la méthode `AcquireConnection` du gestionnaire de connexions ODBC à partir du code managé, parce qu'elle renvoie un objet natif. Par conséquent, cet exemple utilise la chaîne de connexion du gestionnaire de connexions pour se connecter directement à la source de données en utilisant le fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour ODBC managé.  
  
-   `OdbcCommand` attend des paramètres positionnels. Les positions des paramètres sont indiquées par les points d'interrogation (?) dans le texte de la commande. (Par opposition, `SqlCommand` attend des paramètres nommés.)  
  
 Cet exemple utilise la table **Person.Address** de l’exemple de base de données **AdventureWorks**. L’exemple passe la première et la quatrième colonne, les colonnes **int * AddressID*** et **nvarchar (30) City** , de cette table dans le Workflow. Ces mêmes données sont utilisées dans les exemples de sources, transformations et destinations de la rubrique [Développement de types spécifiques de composants Script](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Pour configurer cet exemple de composant Script  
  
1.  Créez un gestionnaire de connexions ODBC qui se connecte à la base de données **AdventureWorks**.  
  
2.  Créez une table de destination en exécutant la commande Transact-SQL suivante dans la base de données **AdventureWorks** :  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  Ajoutez un nouveau composant Script à l'aire du concepteur de flux de données et configurez-le en tant que destination.  
  
4.  Connectez la sortie d'une source ou transformation en amont au composant de destination dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Vous pouvez connecter directement une source à une destination sans transformation.) Pour garantir le bon fonctionnement de cet exemple, la sortie du composant en amont doit inclure au moins les colonnes **AddressID** et **City** de la table **Person.Address** de l’exemple de base de données **AdventureWorks**.  
  
5.  Ouvrez l' **Éditeur de transformation de script**. Dans la page **Colonnes d’entrée**, sélectionnez les colonnes **AddressID** et **City**.  
  
6.  Dans la page **Entrées et sorties**, renommez l’entrée en lui attribuant un nom plus descriptif, comme **MyAddressInput**.  
  
7.  Dans la page **Gestionnaires de connexions**, ajoutez ou créez le gestionnaire de connexions ODBC et attribuez-lui un nom descriptif, par exemple **MyODBCConnectionManager**.  
  
8.  Dans la page **script** , cliquez sur **modifier le script**, puis entrez le script ci-dessous `ScriptMain` dans la classe.  
  
9. Fermez l’environnement de développement de script, fermez l’**Éditeur de transformation de script**, puis exécutez l’exemple.  
  
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
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d'une destination à l'aide du composant Script](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
