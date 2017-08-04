---
title: "Exemple de flux de travail personnalisé (Master Data Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e2b3ad5ab349456364d2aa0af8826dd6970e55b1
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-custom-workflow---example"></a>Créer un flux de travail personnalisé - exemple
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], lorsque vous créez une bibliothèque de classes de flux de travail personnalisé, vous créez une classe qui implémente l’interface Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender. Cette interface inclut une méthode, <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>, appelée par le service d'intégration de flux de travail MDS SQL Server lorsqu'un flux de travail démarre. Le <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> méthode contient deux paramètres : *workflowType* contient le texte que vous avez entré dans le **type de flux de travail** zone de texte [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], et *élément de données* contient les métadonnées et l’élément de données pour l’élément qui a déclenché la règle d’entreprise de flux de travail.  
  
## <a name="custom-workflow-example"></a>Exemple de flux de travail personnalisé  
 L'exemple de code suivant montre comment vous pouvez appliquer la méthode <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> pour extraire les attributs Name, Code et LastChgUserName à partir des données XML pour l'élément qui a déclenché la règle d'entreprise de flux de travail, et comment appeler une procédure stockée pour les insérer dans une autre base de données. Pour obtenir un exemple des données d’élément XML et une explication de son contenu, consultez [Description XML de flux de travail personnalisé &#40; Master Data Services &#41; ](../../master-data-services/develop/create-a-custom-workflow-xml-description.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un flux de travail personnalisé &#40; Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)  
  
  
