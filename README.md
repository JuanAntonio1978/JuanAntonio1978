Inicio[Inicio] --> SeleccionarUnidades;
SeleccionarUnidades --> SolicitarUnidades;
SolicitarUnidades --> PrepararUnidades;
PrepararUnidades --> InformarAvanzada;
InformarAvanzada --> EnviarUnidades;
EnviarUnidades --> RecibirUnidades;
RecibirUnidades --> RevisarUnidades;
RevisarUnidades --> {
    UnidadConDetalle[Detalle OK] --> ReportarGarantia;
    UnidadSinDetalle[Detalle con problema] --> ReportarGarantia;
};

ReportarGarantia --> SolicitudGarantia;
SolicitudGarantia --> ProcesoGarantia;

ProcesoGarantia --> {
    ProcesoVariable[Variable según marca] --> FinalProcesoGarantia;
};

FinalProcesoGarantia --> GenerarCartaPorte;

GenerarCartaPorte --> EntradaUnidadesSistema;
EntradaUnidadesSistema --> AsignarNumeroInventario;
AsignarNumeroInventario --> ContabilizarERP;
ContabilizarERP --> RecibirFacturas;
RecibirFacturas --> ProcesoPago;
ProcesoPago --> RegistrarInventarioPropio;
RegistrarInventarioPropio --> GestionarPago;
GestionarPago --> FinalizarProceso;

FinalizarProceso --> Fin[Fin];
