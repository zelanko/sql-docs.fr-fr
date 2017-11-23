---
title: "Le traitement XML du côté Client (la Classes managées SQLXML) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 742da499fa4d3e7e8d9334af51a0a616c48a7c55
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a>traitement du XML côté client (classes managées SQLXML)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Cet exemple illustre l’utilisation de la propriété ClientSideXml. L'application exécute une procédure stockée sur le serveur. Le résultat de la procédure stockée (un ensemble de lignes à deux colonnes) est traité sur le côté client pour produire un document XML.  
  
 Le GetContacts suivant procédure stockée renvoie **FirstName** et **LastName** des employés de la table Person.Contact dans la base de données AdventureWorks.  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 Cette application c# exécute la procédure stockée et spécifie l’option FOR XML AUTO en spécifiant la valeur CommandText. Dans l’application, la propriété ClientSideXml de l’objet SqlXmlCommand est définie sur true. Cela vous permet d'exécuter les procédures stockées préexistantes qui retournent un ensemble de lignes et lui appliquent une transformation XML.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
    static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
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
  
 Pour tester cet exemple, le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework doit être installé sur votre ordinateur.  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Créez la procédure stockée.  
  
2.  Enregistrez le code C# (DocSample.cs) fourni dans cet exemple dans un dossier. Modifiez le code pour spécifier les informations de connexion et de mot de passe appropriées.  
  
3.  Compilez le code. Pour compiler le code à l'invite de commandes, utilisez :  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Un fichier exécutable (DocSample.exe) est alors créé.  
  
4.  À l'invite de commandes, exécutez DocSample.exe.  
  
  
