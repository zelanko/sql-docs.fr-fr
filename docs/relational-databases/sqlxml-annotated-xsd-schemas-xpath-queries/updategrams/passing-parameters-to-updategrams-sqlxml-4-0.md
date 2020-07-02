---
title: Passage de paramètres à codes (SQLXML)
description: Découvrez comment transmettre des paramètres à codes dans SQLXML 4,0.
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nullvalue attribute
- passing parameters [SQLXML]
- parameters [SQLXML]
- updategrams [SQLXML], passing parameters
- null values [SQLXML]
ms.assetid: 2354e6e7-1860-471f-8711-4e374c5a4ed2
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ce7be0a6f01ac92f13f35e4410dc59601fdbdc01
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85790558"
---
# <a name="passing-parameters-to-updategrams-sqlxml-40"></a>Passage de paramètres aux codes de mise à jour (updategrams) (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Les codes de mise à jour sont des modèles ; par conséquent, vous pouvez leur passer des paramètres. Pour plus d’informations sur le passage de paramètres à des modèles, consultez Considérations sur la [sécurité mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md).  
  
 Les codes de mise à jour vous permettent de passer NULL comme valeur de paramètre. Pour passer la valeur de paramètre NULL, vous spécifiez l’attribut **NullValue** . La valeur assignée à l’attribut **NullValue** est ensuite fournie comme valeur de paramètre. Les codes de mise à jour traitent cette valeur comme NULL.  
  
> [!NOTE]  
>  Dans **\<sql:header>** et **\<updg:header>** , vous devez spécifier **NullValue** comme Unqualified ; alors que, **\<updg:sync>** dans, vous spécifiez **NullValue** comme Qualified (par exemple, **attribut updg : NullValue**).  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l’aide des exemples suivants, vous devez respecter les exigences spécifiées dans la [Configuration requise pour l’exécution d’exemples SQLXML](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
 Avant d'utiliser les exemples de code de mise à jour, notez les points suivants :  
  
-   Les exemples utilisent le mappage par défaut (en d'autres termes, aucun schéma de mappage n'est spécifié dans le code de mise à jour (updategram)). Pour obtenir plus d’exemples de codes qui utilisent des schémas de mappage, consultez [spécification d’un schéma de mappage annoté dans un mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
### <a name="a-passing-parameters-to-an-updategram"></a>A. Passage de paramètres à un code de mise à jour  
 Dans cet exemple, le code de mise à jour modifie le nom d'un employé dans la table HumanResources.Shift. Deux paramètres sont passés au code de mise à jour : ShiftID, utilisé pour identifier un horaire de travail de manière unique, et Nom.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header>  
  <updg:param name="ShiftID"/>  
  <updg:param name="Name" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="$ShiftID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="$Name" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Copiez le code de mise à jour ci-dessus dans le Bloc-notes et enregistrez-le sous le nom UpdategramWithParameters.xml.  
  
2.  Préparez le script de test SQLXML 4,0 (Sqlxml4test. vbs) dans [à l’aide d’ADO pour exécuter des requêtes sqlxml 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) afin d’exécuter le mise à jour en ajoutant les lignes suivantes après `cmd.Properties("Output Stream").Value = outStream` :  

    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value  
    cmd.Parameters.Append cmd.CreateParameter("@ShiftID",  2, 1,  0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@Name",   200, 1, 50, "New Name")  
    ```  
  
### <a name="b-passing-null-as-a-parameter-value-to-an-updategram"></a>B. Passage de NULL comme valeur de paramètre à un code de mise à jour  
 Lors de l'exécution d'un code de mise à jour, la valeur « isnull » est assignée au paramètre auquel vous souhaitez affecter la valeur NULL. Le code de mise à jour convertit la valeur de paramètre « isnull » en NULL et la traite en conséquence.  
  
 Le code de mise à jour suivant affecte la valeur NULL à un titre d'employé :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header nullvalue="isnull" >  
  <updg:param name="EmployeeID"/>  
  <updg:param name="ManagerID" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Employee EmployeeID="$EmployeeID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Employee ManagerID="$ManagerID" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Copiez le code de mise à jour ci-dessus dans le Bloc-notes et enregistrez-le sous le nom UpdategramPassingNullvalues.xml.  
  
2.  Préparez le script de test SQLXML 4,0 (Sqlxml4test. vbs) dans [à l’aide d’ADO pour exécuter des requêtes sqlxml 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) afin d’exécuter le mise à jour en ajoutant les lignes suivantes après `cmd.Properties("Output Stream").Value = outStream` :  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value   
    cmd.Parameters.Append cmd.CreateParameter("@EmployeeID", 3, 1, 0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@ManagerID",  3, 1, 0, Null)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
