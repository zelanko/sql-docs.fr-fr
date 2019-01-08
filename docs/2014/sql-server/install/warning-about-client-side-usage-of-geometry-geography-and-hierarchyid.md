---
title: Avertissement concernant l’utilisation du côté client de GEOMETRY, GEOGRAPHY et HIERARCHYID | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d9ee14c39f7fee577065de934f839f9d6c88e630
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52413769"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a>Avertissement sur l'utilisation du côté client de GEOMETRY, de la GÉOGRAPHIE et du HIERARCHYID
  L’assembly **Microsoft.SqlServer.Types.dll**, qui contient les types de données spatiales, a été mis à niveau de la version 10.0 vers la version 11.0. Les applications personnalisées qui font référence à cet assembly peuvent échouer lorsque certaines conditions sont vraies.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 L’assembly **Microsoft.SqlServer.Types.dll**, qui contient les types de données spatiales, a été mis à niveau de la version 10.0 vers la version 11.0. Les applications personnalisées qui font référence à cet assembly peuvent échouer lorsque les conditions suivantes sont remplies.  
  
-   Lorsque vous déplacez une application personnalisée à partir d’un ordinateur sur lequel [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] a été installé sur un ordinateur sur lequel uniquement [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est installé, l’application échoue, car la version référencée 10.0 de le **SqlTypes** assembly n’est pas présent. Le message d'erreur suivant peut s'afficher : `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`  
  
-   Lorsque vous référencez le **SqlTypes** version 11.0, de l’assembly et la version 10.0 est également installée, vous pouvez voir ce message d’erreur : `"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`  
  
-   Lorsque vous référencez le **SqlTypes** version de l’assembly 11.0 à partir d’une application personnalisée qui cible le .NET 3.5, 4 ou 4.5, l’application échoue, car SqlClient charge la version 10.0 de l’assembly. Cette erreur se produit lorsque l'application appelle l'une des méthodes suivantes :  
  
    -   méthode `GetValue` de la classe `SqlDataReader`  
  
    -   méthode `GetValues` de la classe `SqlDataReader`  
  
    -   opérateur d'index de crochets [] de la classe `SqlDataReader`  
  
    -   méthode `ExecuteScalar` de la classe `SqlCommand`  
  
## <a name="corrective-action"></a>Action corrective  
 Vous pouvez contourner ce problème en utilisant l’une des méthodes suivantes :  
  
-   Vous pouvez contourner ce problème dans votre code en appelant la méthode `GetSqlBytes`, au lieu des méthodes Get répertoriées ci-dessus, pour extraire les types de systèmes CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], comme le montre l'exemple suivant :  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   Vous pouvez contourner ce problème en utilisant la redirection d'assembly dans le fichier de configuration de l'application, comme le montre l'exemple suivant :  
  
    ```xml  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    ```  
  
-   Vous pouvez contourner ce problème dans votre chaîne de connexion en spécifiant la valeur « SQL Server 2012 » pour que de l'attribut « Type System Version » force SqlClient à charger la version 11.0 de l'assembly. Cet attribut de chaîne de connexion est uniquement disponible dans le .NET 4.5 et versions ultérieures.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
