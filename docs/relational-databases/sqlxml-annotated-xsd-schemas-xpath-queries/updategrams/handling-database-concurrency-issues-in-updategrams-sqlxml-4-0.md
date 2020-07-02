---
title: Problèmes d’accès concurrentiel à la base de données dans codes (SQLXML)
description: Découvrez comment utiliser le mécanisme de contrôle d’accès concurrentiel optimiste dans codes (SQLXML 4,0) pour gérer les problèmes d’accès concurrentiel de la base de données.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <before> block
- low concurrency protection
- database concurrency [SQLXML]
- timestamp column [SQLXML]
- updategrams [SQLXML], database concurrency
- high concurrency protection [SQLXML]
- optimistic concurrency control
- concurrency [SQLXML]
- intermediate concurrency protection [SQLXML]
ms.assetid: d4b908d1-b25b-4ad9-8478-9cd882e8c44e
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 11e4a7a875dd2c9b9450619f389b2f082136c536
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85790590"
---
# <a name="handling-database-concurrency-issues-in-updategrams-sqlxml-40"></a>Gestion des problèmes d'accès concurrentiel aux bases de données dans les codes de mise à jour (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Comme d'autres mécanismes de mise à jour de base de données, les codes de mise à jour doivent faire face à des mises à jour simultanées de données dans un environnement multi-utilisateur. Les codes de mise à jour utilisent le contrôle d'accès concurrentiel optimiste, qui utilise la comparaison des données de champ sélectionnées comme instantanés pour garantir que les données à mettre à jour n'ont pas été altérées par une autre application utilisateur depuis qu'elles ont été lues à partir de la base de données. Codes inclut ces valeurs d’instantané dans le **\<before>** bloc du codes. Avant de mettre à jour la base de données, le mise à jour vérifie les valeurs spécifiées dans le **\<before>** bloc par rapport aux valeurs actuellement présentes dans la base de données pour s’assurer que la mise à jour est valide.  
  
 Le contrôle d'accès concurrentiel optimiste offre trois niveaux de protection dans un code de mise à jour : bas (aucune), intermédiaire et haut. Vous pouvez décider de quel niveau de protection vous avez besoin en spécifiant le code de mise à jour en conséquence.  
  
## <a name="lowest-level-of-protection"></a>Niveau de protection le plus bas  
 Ce niveau correspond à une mise à jour aveugle, dans laquelle la mise à jour est traitée sans se référer aux autres mises à jour effectuées depuis la dernière lecture de la base de données. Dans ce cas, vous spécifiez uniquement la ou les colonnes de clé primaire dans le **\<before>** bloc pour identifier l’enregistrement et vous spécifiez les informations mises à jour dans le **\<after>** bloc.  
  
 Par exemple, le nouveau numéro de téléphone du contact dans le code de mise à jour suivant est correct, indépendamment de ce que le numéro de téléphone était précédemment. Notez que le **\<before>** bloc spécifie uniquement la colonne de clé primaire (ContactID).  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="intermediate-level-of-protection"></a>Niveau de protection intermédiaire  
 Dans ce niveau de protection, le code de mise à jour compare la ou les valeurs actuelles des données qui sont mises à jour avec la ou les valeurs présentes dans la ou les colonnes de la base de données pour garantir que les valeurs n'ont pas été modifiées par quelque autre transaction depuis que l'enregistrement a été lu par votre transaction.  
  
 Vous pouvez bénéficier de ce niveau de protection en spécifiant la ou les colonnes de clé primaire et la ou les colonnes que vous mettez à jour dans le **\<before>** bloc.  
  
 Par exemple, ce code de mise à jour modifie la valeur dans la colonne Phone de la table Person.Contact pour le contact dont ContactID a la valeur 1. Le **\<before>** bloc spécifie l’attribut **Phone** pour garantir que cette valeur d’attribut correspond à la valeur de la colonne correspondante dans la base de données avant d’appliquer la valeur mise à jour.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" Phone="398-555-0132" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="high-level-of-protection"></a>Niveau de protection élevé  
 Un niveau de protection élevé garantit qu'un enregistrement reste le même depuis que votre application a lu pour la dernière fois cet enregistrement (autrement dit, depuis que votre application a lu l'enregistrement, celui-ci n'a été modifié par aucune autre transaction).  
  
 Il existe deux façons d'obtenir ce niveau de protection élevé contre les mises à jour simultanées :  
  
-   Spécifiez des colonnes supplémentaires dans la table du **\<before>** bloc.  
  
     Si vous spécifiez des colonnes supplémentaires dans le **\<before>** bloc, mise à jour compare les valeurs spécifiées pour ces colonnes aux valeurs qui se trouvaient dans la base de données avant d’appliquer la mise à jour. Si l'une quelconque des colonnes d'enregistrement a changé depuis que votre transaction a lu l'enregistrement, le code de mise à jour n'effectue pas la mise à jour.  
  
     Par exemple, le mise à jour suivant met à jour le nom de l’équipe, mais spécifie des colonnes supplémentaires (StartTime, EndTime) dans le **\<before>** bloc, ce qui demande un niveau de protection supérieur contre les mises à jour simultanées.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1"   
                 Name="Day"   
                 StartTime="1900-01-01 07:00:00.000"   
                 EndTime="1900-01-01 15:00:00.000" />  
    </updg:before>  
    <updg:after>  
       <HumanResources.Shift Name="Morning" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
     Cet exemple spécifie le niveau de protection le plus élevé en spécifiant toutes les valeurs de colonne de l’enregistrement dans le **\<before>** bloc.  
  
-   Spécifiez la colonne timestamp (si disponible) dans le **\<before>** bloc.  
  
     Au lieu de spécifier toutes les colonnes d’enregistrement dans le \<before**> bloc * *, vous pouvez simplement spécifier la colonne timestamp (si la table en a une) avec la ou les colonnes de clé primaire dans le **\<before>** bloc. La base de données met à jour la colonne timestamp en spécifiant une valeur unique après chaque mise à jour de l'enregistrement. Dans ce cas, le code de mise à jour compare la valeur de l'horodateur avec la valeur correspondante dans la base de données. La valeur d'horodateur stockée dans la base de données est une valeur binaire. Par conséquent, la colonne timestamp doit être spécifiée dans le schéma sous la forme **DT : type = "bin. Hex"**, **DT : type = "bin. base64"** ou **SQL : datatype = "timestamp"**. (Vous pouvez spécifier soit le type de données **XML** , soit le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type de données.)  
  
#### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Créez cette table dans la base de données **tempdb** :  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (  
                 CustomerID  varchar(5),  
                 ContactName varchar(20),  
                 LastUpdated timestamp)  
    ```  
  
2.  Ajoutez cet exemple d'enregistrement :  
  
    ```  
    INSERT INTO Customer (CustomerID, ContactName) VALUES   
                         ('C1', 'Andrew Fuller')  
    ```  
  
3.  Copiez le schéma XSD suivant et collez-le dans le Bloc-notes. Enregistrez-le sous le nom ConcurrencySampleSchema.xml :  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Customer" sql:relation="Customer" >  
       <xsd:complexType>  
            <xsd:attribute name="CustomerID"    
                           sql:field="CustomerID"   
                           type="xsd:string" />   
  
            <xsd:attribute name="ContactName"    
                           sql:field="ContactName"   
                           type="xsd:string" />  
  
            <xsd:attribute name="LastUpdated"   
                           sql:field="LastUpdated"   
                           type="xsd:hexBinary"   
                 sql:datatype="timestamp" />  
  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
4.  Copiez le code de mise à jour ci-dessous dans le Bloc-notes et enregistrez-le sous le nom ConcurrencySampleTemplate.xml dans le répertoire où vous avez enregistré le schéma créé à l'étape précédente. (Notez que la valeur d'horodateur ci-dessous pour LastUpdated différera dans votre exemple de table Customer et copiez donc la valeur réelle pour LastUpdated à partir de la table et collez-la dans le code de mise à jour.)  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
    <updg:before>  
       <Customer CustomerID="C1"   
                 LastUpdated = "0x00000000000007D1" />  
    </updg:before>  
    <updg:after>  
       <Customer ContactName="Robert King" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
5.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le schéma XDR équivalent :  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<ElementType name="Customer" sql:relation="Customer" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="ContactName" />  
    <AttributeType name="LastUpdated"  dt:type="bin.hex"   
                                       sql:datatype="timestamp" />  
    <attribute type="CustomerID" />  
    <attribute type="ContactName" />  
    <attribute type="LastUpdated" />  
</ElementType>  
</Schema>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
