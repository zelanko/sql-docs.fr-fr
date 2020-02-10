---
title: Exécution de requêtes SQL (classes managées SQLXML) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteToStream method
- SQL queries [SQLXML]
ms.assetid: a561ae83-a8b6-4b9b-a819-9b86839546b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f8e16ff3651b9ce23fafe99137b4905eb3961ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014942"
---
# <a name="executing-sql-queries-sqlxml-managed-classes"></a>Exécution de requêtes SQL (classes managées SQLXML)
  Cet exemple illustre les éléments suivants :  
  
-   Création de paramètres (objets SqlXmlParameter).  
  
-   Affectation de valeurs aux propriétés (nom et valeur) des objets SqlXmlParameter.  
  
 Dans cet exemple, une simple requête SQL est exécutée dans le but d'extraire le prénom, le nom et la date de naissance de l'employé dont la valeur désignant le nom est passée en tant que paramètre. En spécifiant le paramètre (*LastName*), seule la propriété Value est définie. La propriété Name n’est pas définie, car dans cette requête, le paramètre est positionnel et aucun nom n’est requis.  
  
 La propriété CommandType de l’objet SqlXmlCommand par défaut est **SQL**. Par conséquent, la propriété n'est pas explicitement définie.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion.  
  
 Voici le code C# :  
  
```  
using System;  
  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);        
         cmd.CommandText = "SELECT FirstName, LastName FROM Person.Contact WHERE LastName=? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         string strResult;  
         try   
         {  
            strm = cmd.ExecuteStream();  
            strm.Position = 0;  
            using(StreamReader sr = new StreamReader(strm))  
            {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         catch (SqlXmlException e)  
         {  
            //in case of an error, this prints error returned.  
            e.ErrorStream.Position=0;  
            strResult=new StreamReader(e.ErrorStream).ReadToEnd();  
            System.Console.WriteLine(strResult);  
         }  
  
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
  
1.  Enregistrez dans un dossier le code C# (DocSample.cs) fourni dans cette rubrique.  
  
2.  Compilez le code. Pour compiler le code à l'invite de commandes, utilisez :  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Un fichier exécutable (DocSample.exe) est alors créé.  
  
3.  À l'invite de commandes, exécutez DocSample.exe.  
  
 Pour tester cet exemple, le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework doit être installé sur votre ordinateur.  
  
 Au lieu de spécifier des requêtes SQL en tant que texte de commande, vous pouvez spécifier un modèle (comme illustré dans le fragment de code ci-après) qui exécute un code de mise à jour (ou « updategram », lequel est également un modèle) afin d'insérer un enregistrement de client. Vous pouvez spécifier des modèles et des codes de mise à jour dans les fichiers et exécuter des fichiers. Pour plus d’informations, consultez [exécution de fichiers modèles à l’aide de la propriété CommandText](executing-template-files-by-using-the-commandtext-property.md).  
  
```  
SqlXmlCommand cmd = new SqlXmlCommand("Provider=SQLOLEDB;Data Source=SqlServerName;Initial Catalog=Database; Integrated Security=SSPI;");  
Stream stm;  
cmd.CommandType = SqlXmlCommandType.UpdateGram;  
cmd.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' xmlns:updg='urn:schemas-microsoft-com:xml-updategram'>" +  
      "<updg:sync>" +  
       "<updg:before/>" +  
       "<updg:after>" +  
         "<Customer CustomerID='aaaaa' CustomerName='Some Name' CustomerTitle='SomeTitle' />" +  
       "</updg:after>" +  
       "</updg:sync>" +  
       "</ROOT>";  
  
stm = cmd.ExecuteStream();  
stm = null;  
cmd = null;  
```  
  
## <a name="using-executetostream"></a>Utilisation de la méthode ExecuteToStream  
 Si vous disposez d’un flux existant, vous pouvez utiliser la méthode ExecuteToStream au lieu de créer un objet de flux et d’utiliser la méthode Execute. Le code de l’exemple précédent est révisé ici pour utiliser la méthode ExecuteToStream :  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlParameter p;  
      MemoryStream ms = new MemoryStream();  
      StreamReader sr = new StreamReader(ms);  
      ms.Position = 0;  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.CommandText = "select FirstName, LastName from Person.Contact where LastName = ? For XML Auto";  
      p = cmd.CreateParameter();  
      p.Value = "Achong";  
      cmd.ExecuteToStream(ms);  
      ms.Position = 0;  
      Console.WriteLine(sr.ReadToEnd());  
      return 0;        
   }  
   public static int Main(String[] args)  
   {  
      testParams();     
      return 0;  
   }  
}  
```  
  
> [!NOTE]  
>  Vous pouvez également utiliser le ExecuteXMLReadermethod qui retourne un objet XmlReader. Pour plus d’informations, consultez [exécution de requêtes SQL à l’aide de la méthode ExecuteXmlReader](executing-sql-queries-by-using-the-executexmlreader-method.md).  
  
  
