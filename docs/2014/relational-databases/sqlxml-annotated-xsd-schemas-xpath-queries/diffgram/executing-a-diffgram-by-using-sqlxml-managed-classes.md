---
title: Exécution d’un DiffGram à l’aide de classes managées SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], Managed Classes
- SQLXML Managed Classes, DiffGrams
- Managed Classes [SQLXML], DiffGrams
- SQLXML, Managed Classes
ms.assetid: 81c687ca-8c9f-4f58-801f-8dabcc508a06
author: rothja
ms.author: jroth
ms.openlocfilehash: 117a6e90541c22489f225d27dd2c0c8b498c81f9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062962"
---
# <a name="executing-a-diffgram-by-using-sqlxml-managed-classes"></a>Exécution d'un DiffGram à l'aide des classes managées SQLXML
  Cet exemple montre comment exécuter un fichier DiffGram dans l' [!INCLUDE[msCoName](../../../includes/msconame-md.md)] environnement .NET Framework pour appliquer des mises à jour de données à des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables à l’aide de classes managées SQLXML (Microsoft. Data. SQLXML).  
  
 Dans cet exemple, le DiffGram met à jour les informations sur les clients (CompanyName et ContactName) pour le client ALFKI.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer1"   
                msdata:rowOrder="0" diffgr:hasChanges="modified"   
                CustomerID="ALFKI">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Antonio Moreno</ContactName>  
      </Customer>  
    </DataInstance>  
    <diffgr:before>  
     <Customer diffgr:id="Customer1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
    </diffgr:before>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 Le **\<before>** bloc comprend un **\<Customer>** élément (**diffgr : ID = "Customer1"**). Le **\<DataInstance>** bloc comprend l' **\<Customer>** élément correspondant avec le même **ID**. L' **\<customer>** élément dans le **\<NewDataSet>** spécifie également **diffgr : hasChanges = "modified"**. Cela indique une opération de mise à jour et l'enregistrement de client de la table Cust est mis à jour en conséquence. Notez que si l’attribut **diffgr : hasChanges** n’est pas spécifié, la logique de traitement DiffGram ignore cet élément et aucune mise à jour n’est effectuée.  
  
 Voici le code d’une application didacticiel C# qui montre comment utiliser les classes managées SQLXML pour exécuter le DiffGram ci-dessus et mettre à jour deux tables (cust, ORD) que vous allez également créer dans la base de données **tempdb** .  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=MyServer;database=tempdb;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlAdapter ad;  
      // Need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandStream = new FileStream("MyDiffgram.xml", FileMode.Open, FileAccess.Read);  
      cmd.CommandType = SqlXmlCommandType.DiffGram;  
      cmd.SchemaPath = "DiffGramSchema.xml";  
      // Load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      ad.Update(ds);  
      return 0;  
   }  
   public static int Main(String[] args)  
   {  
      testParams();  
      return 0;  
   }  
}  
```  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Vérifiez que le .NET Framework est installé sur votre ordinateur.  
  
2.  Enregistrez le schéma XSD suivant (DiffGramSchema.xml) dans un dossier :  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
     <xsd:annotation>  
      <xsd:documentation>  
        Diffgram Customers/Orders Schema.  
      </xsd:documentation>  
      <xsd:appinfo>  
           <sql:relationship name="CustomersOrders"   
                      parent="Cust"  
                      parent-key="CustomerID"  
                      child-key="CustomerID"  
                      child="Ord"/>  
      </xsd:appinfo>  
     </xsd:annotation>  
     <xsd:element name="Customer" sql:relation="Cust">  
      <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="CompanyName"    type="xsd:string"/>  
          <xsd:element name="ContactName"    type="xsd:string"/>  
           <xsd:element name="Order" sql:relation="Ord" sql:relationship="CustomersOrders">  
            <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:int" sql:field="OrderID"/>  
              <xsd:attribute name="CustomerID" type="xsd:string"/>  
            </xsd:complexType>  
          </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID" type="xsd:string" sql:field="CustomerID"/>  
      </xsd:complexType>  
     </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  Créez ces tables dans la base de données **tempdb** .  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
4.  Ajoutez les exemples de données suivants :  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
5.  Copiez le DiffGram ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom MyDiffGram.xml dans le même dossier qu'à l'étape 1.  
  
6.  Enregistrez le code C# (DiffgramSample.cs) fourni ci-dessus dans le même dossier que celui dans lequel DiffGramSchema.xml et MyDiffGram.xml ont été stockés dans les étapes précédentes.  
  
    > [!NOTE]  
    >  Vous devrez remplacer le nom '`MyServer`' de l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de la chaîne de connexion par le nom réel de votre instance installée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
     Si vous stockez les fichiers dans un dossier différent, vous devrez modifier le code et spécifier le chemin d'accès approprié au répertoire pour le schéma de mappage.  
  
7.  Compilez le code. Pour compiler le code à l'invite de commandes, utilisez :  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DiffgramSample.cs  
    ```  
  
     Un fichier exécutable (DiffgramSample.exe) est alors créé.  
  
8.  À l'invite de commandes, exécutez DiffgramSample.exe.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples DiffGram &#40;SQLXML 4,0&#41;](diffgram-examples-sqlxml-4-0.md)  
  
  
