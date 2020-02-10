---
title: Déclenchement d’événements dans la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- events [Integration Services], scripts
- warnings [Integration Services]
- SSIS events, scripts
- errors [Integration Services], events
- SSIS Script task, events
- Events property
- Script task [Integration Services], events
ms.assetid: 21ea07d1-e267-4fb1-a6cc-82c95a39beae
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 49c288ffd90406e2b657c1bcb58b6c2b741b9142
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62894578"
---
# <a name="raising-events-in-the-script-task"></a>Déclenchement d'événements dans la tâche de script
  Les événements offrent un moyen de signaler des erreurs, des avertissements et d'autres informations, telles que la progression ou l'état d'une tâche, au package conteneur. Le package fournit des gestionnaires d'événements pour gérer les notifications d'événements. La tâche de script peut déclencher des événements en appelant des méthodes sur la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> de l'objet `Dts`. Pour plus d’informations sur la manière dont les packages [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] gèrent les événements, consultez [Gestionnaires d’événements Integration Services &#40;SSIS&#41;](../../integration-services-ssis-event-handlers.md).  
  
 Les événements peuvent être journalisés dans tout module fournisseur d'informations activé dans le package. Les modules fournisseurs d'informations stockent des informations à propos des événements dans une banque de données. La tâche de script peut également utiliser la méthode <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> pour journaliser des informations dans un module fournisseur d'informations sans déclencher d'événement. Pour plus d’informations sur la manière d’utiliser la méthode <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>, consultez [Journalisation dans la tâche de script](logging-in-the-script-task.md).  
  
 Pour déclencher un événement, la tâche de script appelle l'une des méthodes exposées par la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>. Le tableau suivant répertorie les méthodes exposées par la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>.  
  
|Événement|Description|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>|Déclenche un événement personnalisé défini par l'utilisateur dans le package.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A>|Informe le package d'une condition d'erreur.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireInformation%2A>|Fournit des informations à l'utilisateur.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A>|Informe le package de la progression de la tâche.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireQueryCancel%2A>|Retourne une valeur qui indique si le package nécessite l'arrêt prématuré de la tâche.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A>|Informe le package que la tâche est dans un état qui garantit la notification de l'utilisateur, mais qui n'est pas une condition d'erreur.|  
  
## <a name="events-example"></a>Exemples d'événements  
 L'exemple suivant montre comment déclencher des événements à partir de la tâche de script. L'exemple utilise une fonction API Windows native pour déterminer si une connexion Internet est disponible. Si aucune connexion n'est disponible, il génère une erreur. Si une connexion par modem potentiellement volatile est en cours d'utilisation, l'exemple déclenche un avertissement. Sinon, il retourne un message d'information indiquant qu'une connexion Internet a été détectée.  
  
```vb  
Private Declare Function InternetGetConnectedState Lib "wininet" _  
    (ByRef dwFlags As Long, ByVal dwReserved As Long) As Long  
  
Private Enum ConnectedStates  
    LAN = &H2  
    Modem = &H1  
    Proxy = &H4  
    Offline = &H20  
    Configured = &H40  
    RasInstalled = &H10  
End Enum  
  
Public Sub Main()  
  
    Dim dwFlags As Long  
    Dim connectedState As Long  
    Dim fireAgain as Boolean  
  
    connectedState = InternetGetConnectedState(dwFlags, 0)  
  
    If connectedState <> 0 Then  
        If (dwFlags And ConnectedStates.Modem) = ConnectedStates.Modem Then  
            Dts.Events.FireWarning(0, "Script Task Example", _  
                "Volatile Internet connection detected.", String.Empty, 0)  
        Else  
            Dts.Events.FireInformation(0, "Script Task Example", _  
                "Internet connection detected.", String.Empty, 0, fireAgain)  
        End If  
    Else  
        ' If not connected to the Internet, raise an error.  
        Dts.Events.FireError(0, "Script Task Example", _  
            "Internet connection not available.", String.Empty, 0)  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
using System.Runtime.InteropServices;  
  
public class ScriptMain  
{  
  
[DllImport("wininet")]  
        private extern static long InternetGetConnectedState(ref long dwFlags, long dwReserved);  
  
        private enum ConnectedStates  
        {  
            LAN = 0x2,  
            Modem = 0x1,  
            Proxy = 0x4,  
            Offline = 0x20,  
            Configured = 0x40,  
            RasInstalled = 0x10  
        };  
  
        public void Main()  
        {  
            //  
            long dwFlags = 0;  
            long connectedState;  
            bool fireAgain = true;  
            int state;  
  
            connectedState = InternetGetConnectedState(ref dwFlags, 0);  
            state = (int)ConnectedStates.Modem;  
            if (connectedState != 0)  
            {  
                if ((dwFlags & state) == state)  
                {  
                    Dts.Events.FireWarning(0, "Script Task Example", "Volatile Internet connection detected.", String.Empty, 0);  
                }  
                else  
                {  
                    Dts.Events.FireInformation(0, "Script Task Example", "Internet connection detected.", String.Empty, 0, ref fireAgain);  
                }  
            }  
            else  
            {  
                // If not connected to the Internet, raise an error.  
                Dts.Events.FireError(0, "Script Task Example", "Internet connection not available.", String.Empty, 0);  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
```  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaires d’événements Integration Services &#40;SSIS&#41](../../integration-services-ssis-event-handlers.md)   
 [Ajouter un gestionnaire d’événements à un package](../../add-an-event-handler-to-a-package.md)  
  
  
