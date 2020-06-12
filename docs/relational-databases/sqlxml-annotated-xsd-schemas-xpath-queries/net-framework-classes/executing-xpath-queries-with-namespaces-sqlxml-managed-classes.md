---
title: Exécution de requêtes XPath avec des espaces de noms (SQLXML)
description: Découvrez comment inclure des espaces de noms dans des requêtes XPath SQLXML.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces property
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- XPath queries [SQLXML], namespaces
- Managed Classes [SQLXML], executing XPath queries
- SQLXML Managed Classes, executing XPath queries
- namespaces [SQLXML], XPath queries
ms.assetid: c6fc46d8-6b42-4992-a8f1-a8d4b8886e6e
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ee37e30506eb9b41d3b94b2f76f1cf6a5149e6a2
ms.sourcegitcommit: 5b7457c9d5302f84cc3baeaedeb515e8e69a8616
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83688740"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxml-managed-classes"></a>Exécution de requêtes XPath avec des espaces de noms (classes managées SQLXML)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les requêtes XPath peuvent inclure des espaces de noms. Si les éléments de schéma sont qualifiés par un espace de noms (utilisent un espace de noms cible), les requêtes XPath sur le schéma doivent spécifier cet espace de noms.  
  
 Le caractère générique (*) n'étant pas prise en charge dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, vous devez spécifier la requête XPath en utilisant un préfixe d'espace de noms. Pour résoudre le préfixe, utilisez la propriété Namespaces pour spécifier la liaison d’espace de noms.  
  
 Dans l’exemple suivant, la requête XPath spécifie des espaces de noms à l’aide du caractère générique ( \* ) et des fonctions XPath local name () et namespace-URI (). Cette requête XPath retourne tous les éléments dont le nom local est **Employee** et l’URI de l’espace de noms est **urn : MySchema : contacts**:  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 Dans SQLXML 4.0, spécifiez cette requête XPath avec un préfixe d'espace de noms. Par exemple, **x :contact**, où **x** est le préfixe d’espace de noms. Prenons le schéma XSD suivant :  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 Comme ce schéma définit l'espace de noms cible, une requête Xpath (telle que « Employee ») sur ce schéma doit inclure l'espace de noms.  
  
 L'exemple d'application C# suivant exécute une requête XPath sur le schéma XSD précédent (MySchema.xml). Pour résoudre le préfixe, spécifiez la liaison d’espace de noms à l’aide de la propriété namespaces de l’objet SqlXmlCommand.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXPath()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "x:Contact[@CID='1']";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.Namespaces = "xmlns:x='urn:myschema:Contacts'";  
         cmd.SchemaPath = "MySchema.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXPath();  
         return 0;  
      }  
   }  
```  
  
 Pour tester cet exemple, le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework doit être installé sur votre ordinateur.  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Enregistrez dans un dossier le schéma XSD (MySchema.xml) fourni dans cet exemple.  
  
2.  Enregistrez le code C# (DocSample.cs) fourni dans cet exemple dans le même dossier que celui dans lequel le schéma est stocké. (Si vous stockez les fichiers dans un dossier différent, vous devrez modifier le code et spécifier le chemin d'accès approprié au répertoire pour le schéma de mappage.)  
  
3.  Compilez le code. Pour compiler le code à l'invite de commandes, utilisez :  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Un fichier exécutable (DocSample.exe) est alors créé.  
  
4.  À l'invite de commandes, exécutez DocSample.exe.  

