---
title: Passage de paramètres à codes (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d9e699ea80253934ecc6f3ce744feaed6fd6a392
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047466"
---
# <a name="passing-parameters-to-updategrams-sqlxml-40"></a>Passage de paramètres aux codes de mise à jour (updategrams) (SQLXML 4.0)
  Les codes de mise à jour sont des modèles ; par conséquent, vous pouvez leur passer des paramètres. Pour plus d’informations sur le passage de paramètres à des modèles, consultez Considérations sur la [sécurité mise à jour &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md).  
  
 Les codes de mise à jour vous permettent de passer NULL comme valeur de paramètre. Pour passer la valeur de paramètre NULL, vous spécifiez l'attribut `nullvalue`. La valeur assignée à l'attribut `nullvalue` est ensuite fournie comme valeur de paramètre. Les codes de mise à jour traitent cette valeur comme NULL.  
  
> [!NOTE]  
>  Dans `<sql:header>` et `<updg:header>`, vous devez spécifier `nullvalue` comme non qualifié, tandis que dans `<updg:sync>`, vous spécifiez `nullvalue` comme qualifié (par exemple, `updg:nullvalue`).  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l’aide des exemples suivants, vous devez respecter les exigences spécifiées dans la [Configuration requise pour l’exécution d’exemples SQLXML](../../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
 Avant d'utiliser les exemples de code de mise à jour, notez les points suivants :  
  
-   Les exemples utilisent le mappage par défaut (en d'autres termes, aucun schéma de mappage n'est spécifié dans le code de mise à jour (updategram)). Pour obtenir plus d’exemples de codes qui utilisent des schémas de mappage, consultez [spécification d’un schéma de mappage annoté dans un mise à jour &#40;SQLXML 4,0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
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
  
2.  Préparez le script de test SQLXML 4,0 (Sqlxml4test. vbs) dans [à l’aide d’ADO pour exécuter des requêtes sqlxml 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) afin d’exécuter le mise à jour en ajoutant les lignes suivantes après `cmd.Properties("Output Stream").Value = outStream` :  
  
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
  
2.  Préparez le script de test SQLXML 4,0 (Sqlxml4test. vbs) dans [à l’aide d’ADO pour exécuter des requêtes sqlxml 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) afin d’exécuter le mise à jour en ajoutant les lignes suivantes après `cmd.Properties("Output Stream").Value = outStream` :  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value   
    cmd.Parameters.Append cmd.CreateParameter("@EmployeeID", 3, 1, 0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@ManagerID",  3, 1, 0, Null)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité mise à jour &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
