---
title: Avertissement concernant l’utilisation côté client de GEOMETRy, GEOGRAPHY et HIERARCHYID | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 524400e9c9420fb54447220215d4660874ec6d69
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66091087"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a>Avertissement sur l'utilisation du côté client de GEOMETRY, de la GÉOGRAPHIE et du HIERARCHYID
  L’assembly **Microsoft. SqlServer. types. dll**, qui contient les types de données spatiales, a été mis à niveau de la version 10,0 vers la version 11,0. Les applications personnalisées qui font référence à cet assembly peuvent échouer lorsque certaines conditions sont vraies.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 L’assembly **Microsoft. SqlServer. types. dll**, qui contient les types de données spatiales, a été mis à niveau de la version 10,0 vers la version 11,0. Les applications personnalisées qui font référence à cet assembly peuvent échouer lorsque les conditions suivantes sont remplies.  
  
-   Lorsque vous déplacez une application personnalisée à partir d’un ordinateur [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] sur lequel est installé sur un ordinateur sur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] lequel seul est installé, l’application échoue, car la version référencée 10,0 de l’assembly **SqlTypes** n’est pas présente. Ce message d'erreur peut s'afficher : `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`  
  
-   Lorsque vous référencez l’assembly **SqlTypes** version 11,0 et que la version 10,0 est également installée, le message d’erreur suivant peut s’afficher :`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`  
  
-   Quand vous référencez la version 11,0 de l’assembly **SqlTypes** à partir d’une application personnalisée qui cible .net 3,5, 4 ou 4,5, l’application échoue, car SqlClient par conception charge la version 10,0 de l’assembly. Cette erreur se produit lorsque l'application appelle l'une des méthodes suivantes :  
  
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
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md
)  
  
  
