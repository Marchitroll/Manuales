# Solución al error

En esta sección veremos cómo solucionar el siguiente error:

![](/imagenes/politicasEjecucion1.png)

## Requisitos

Para solucionar este problema necesitamos tener:

1. Permisos de administración
2. [Node.js](/Guias/Guia%20de%20instalacion%20nodeJS.md)

## 1. Abrir una terminal PowerShell en modo administrador

Al abrir una terminal Powershell en modo administrador deberemos ejecutar el siguiente comando para ver las políticas de ejecución:

    Get-ExecutionPolicy -list

![](/imagenes/politicasEjecucion2.png)

## 2. Cambio de políticas de ejecución para "LocalMachine"

Si observamos la fila de `LocalMachine`, notaremos que no tiene una política de ejecución definida. En consecuencia, procederemos a establecer una en `LocalMachine`. Para lograrlo, escribimos el siguiente comando:

    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned

Después de ejecutar el comando, se solicitará confirmar el cambio.

![](/imagenes/politicasEjecucion3.png)

Si deseas corroborar el cambio, vuelve a listar las políticas de ejecución con el comando `Get-ExecutionPolicy -list`

![](/imagenes/politicasEjecucion4.png)

Ahora podremos ver que el problema está solucionado

![](/imagenes/politicasEjecucion5.png)

Con esto quedaría solucionado y podríamos continuar creando la [app con react](/Guias/Guia%20de%20creacion%20de%20una%20app%20con%20React.md).

### Mayor información

Si deseas saber más información acerca de este tema puedes visitar la [página oficial de Microsoft](https://learn.microsoft.com/es-mx/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4)