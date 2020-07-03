---
title: Exemple de flux de travail personnalisé
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 880cf38105bd70198a52c55feec151e163f21c28
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900994"
---
# <a name="create-a-custom-workflow---example"></a>Créer un flux de travail personnalisé - Exemple

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], quand vous créez une bibliothèque de classes personnalisées de flux de travail, vous créez une classe qui implémente l’interface Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender. Cette interface comprend une méthode, [Microsoft. MasterDataServices. WorkflowTypeExtender. IWorkflowTypeExtender. StartWorkflow *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) , qui est appelée par SQL Server Service d’intégration de flux de travail MDS lorsqu’un flux de travail démarre. La méthode [Microsoft. MasterDataServices. WorkflowTypeExtender. IWorkflowTypeExtender. StartWorkflow *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) contient deux paramètres : *WorkflowType* contient le texte que vous avez entré dans la zone de texte **type de flux de travail** dans [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , et *dataElement* contient des métadonnées et des données d’élément pour l’élément qui a déclenché la règle d’entreprise de Workflow.  
  
## <a name="custom-workflow-example"></a>Exemple de flux de travail personnalisé  
 L’exemple de code suivant montre comment implémenter la méthode [Microsoft. MasterDataServices. WorkflowTypeExtender. IWorkflowTypeExtender. StartWorkflow *](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) pour extraire les attributs Name, code et LastChgUserName des données XML pour l’élément qui a déclenché la règle d’entreprise de workflow, et comment appeler une procédure stockée pour les insérer dans une autre base de données. Pour obtenir un exemple de code XML de données d’élément et une explication des indicateurs qu’il contient, consultez [Description du code XML d’un flux de travail personnalisé &#40;Master Data Services&#41;](../../master-data-services/develop/create-a-custom-workflow-xml-description.md).  
  
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
 [Créer un flux de travail personnalisé &#40;Master Data Services&#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)  
  
  
