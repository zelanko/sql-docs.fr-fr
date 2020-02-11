---
title: 'Leçon 3 : charger une définition de rapport à partir du serveur de rapports | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ad8b31c-43b0-4481-a31b-090cbed4a438
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d4c51002c8c829417c63a0dd6c59a3538604fd81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63042512"
---
# <a name="lesson-3-load-a-report-definition-from-the-report-server"></a>Leçon 3 : chargement d'une définition de rapport à partir du serveur de rapports
  Après avoir créé votre projet et généré les classes à partir du schéma RDL, vous êtes prêt à charger une définition du rapport depuis le serveur de rapports.  
  
### <a name="to-load-a-report-definition"></a>Pour charger une définition de rapport  
  
1.  Ajoutez un champ privé en haut de la `ReportUpdater` classe (module si vous utilisez [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) pour la `Report` classe. Ce champ sera utilisé pour conserver une référence au rapport chargé depuis le serveur de rapports pendant la vie de l'application.  
  
    ```csharp  
    private Report _report;  
    ```  
  
    ```vb  
    Private m_report As Report  
    ```  
  
2.  Remplacez le code de la méthode `LoadReportDefinition()` du fichier Program.cs (Module1.vb en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) par le code suivant :  
  
    ```csharp  
    private void LoadReportDefinition()  
    {  
        System.Console.WriteLine("Loading Report Definition");  
  
        string reportPath =   
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        // Retrieve the report definition   
        // from the report server  
        byte[] bytes =   
            _reportService.GetItemDefinition(reportPath);  
  
        if (bytes != null)  
        {  
            XmlSerializer serializer =   
                new XmlSerializer(typeof(Report));  
  
            // Load the report bytes into a memory stream  
            using (MemoryStream stream = new MemoryStream(bytes))  
            {  
                // Deserialize the report stream to an   
                // instance of the Report class  
                _report = (Report)serializer.Deserialize(stream);  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub LoadReportDefinition()  
  
        System.Console.WriteLine("Loading Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
  
        'Retrieve the report definition   
        'from the report server  
        Dim bytes As Byte() = _  
            m_reportService.GetItemDefinition(reportPath)  
  
        If Not (bytes Is Nothing) Then  
  
            Dim serializer As XmlSerializer = _  
                New XmlSerializer(GetType(Report))  
  
            'Load the report bytes into a memory stream  
            Using stream As MemoryStream = New MemoryStream(bytes)  
  
                'Deserialize the report stream to an   
                'instance of the Report class  
                m_report = CType(serializer.Deserialize(stream), _  
                                 Report)  
  
            End Using  
  
        End If  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>Leçon suivante  
 Dans la leçon suivante, vous allez écrire le code permettant de mettre à jour la définition du rapport chargée depuis le serveur de rapports. Consultez [la leçon 4 : mettre à jour la définition de rapport par programmation](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des rapports à l’aide de classes générées à partir du schéma RDL &#40;didacticiel SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Report Definition Language &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
