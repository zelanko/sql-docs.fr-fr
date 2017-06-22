---
title: "Encoder et décoder des identificateurs SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9e5499ddf0c36d277068cb222a5c438c720a4c3a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="encode-and-decode-sql-server-identifiers"></a>Encoder et décoder des identificateurs SQL Server
  Les identificateurs délimités SQL Server contiennent parfois des caractères non pris en charge dans les chemins d'accès Windows PowerShell. Vous pouvez spécifier ces caractères en encodant leurs valeurs hexadécimales.  
  
1.  **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)  
  
2.  **To process special characters:**  [Encoding an Identifier](#EncodeIdent), [Decoding an Identifier](#DecodeIdent)  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Les caractères qui ne sont pas pris en charge dans les noms de chemins d'accès Windows PowerShell peuvent être représentés, ou codés, sous la forme du caractère « % » suivi de la valeur hexadécimale pour le modèle binaire qui représente le caractère, comme dans «**%**xx ». Le codage peut toujours être utilisé pour gérer des caractères qui ne sont pas pris en charge dans les chemins d'accès Windows PowerShell.  
  
 L’applet de commande **Encode-SqlName** prend comme entrée un identificateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Elle génère une chaîne contenant tous les caractères qui ne sont pas pris en charge par le langage Windows PowerShell codés avec « % xx ». L’applet de commande **Decode-SqlName** prend comme entrée un identificateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] encodé et retourne l’identificateur d’origine.  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Les applets de commande **Encode-Sqlname** et **Decode-Sqlname** encodent ou décodent uniquement les caractères autorisés dans les identificateurs délimités SQL Server, mais ne sont pas prises en charge dans les chemins PowerShell. Voici les caractères encodés par **Encode-SqlName** et décodés par **Decode-SqlName**:  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|**Caractère**|\|/|:|%|\<|>|*|?|[|]|&#124;|  
|**Encodage hexadécimal**|%5C|%2F|%3A|%25|%3C|%3E|%2A|%3F|%5B|%5D|%7C|  
  
##  <a name="EncodeIdent"></a> Encodage d'un identificateur  
 **Pour encoder un identificateur SQL Server dans un chemin d'accès PowerShell**  
  
-   Utilisez l'une des deux méthodes suivantes pour encoder un identificateur SQL Server :  
  
    -   Spécifiez le code hexadécimal du caractère non pris en charge à l'aide de la syntaxe %XX, où XX est le code hexadécimal.  
  
    -   Passez l’identificateur en tant que chaîne entre guillemets à l’applet de commande **Encode-Sqlname**  
  
### <a name="examples-encoding"></a>Exemples (encodage)  
 Cet exemple spécifie la version encodée du caractère « : » (%3A) :  
  
```  
Set-Location Table%3ATest  
```  
  
 Vous pouvez également utiliser **Encode-SqlName** pour générer un nom pris en charge par Windows PowerShell :  
  
```  
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="DecodeIdent"></a> Décodage d'un identificateur  
 **Pour décoder un identificateur SQL Server à partir d'un chemin d'accès PowerShell**  
  
 Utilisez l’applet de commande **Decode-Sqlname** pour remplacer les encodages hexadécimaux par les caractères représentés par l’encodage.  
  
### <a name="examples-decoding"></a>Exemples (décodage)  
 Cet exemple retourne « Table:Test » :  
  
```  
Decode-SqlName "Table%3ATest"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Identificateurs SQL Server dans PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [fournisseur PowerShell SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  
