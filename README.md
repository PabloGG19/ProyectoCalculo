# ProyectoCalculo
function spline_prueba1(X,Y)

n=length(X);
for k=1:n-1
    %Cálculo de la pendiente de la recta
    m=(Y(k+1)-Y(k))/(X(k+1)-X(k));
    %Cálculo del término independiente
    b=(k)-m*X(k);
    % Si b es positivo: muestra mx + b
    if b>0
    fprintf('\n%fx+%f \t para x en [%.3f,%.3f]',m,b,X(k),X(k+1))
    % Si b es negativo: muestra mx - |b|
    elseif b<0
    fprintf('\n%fx-%f \t para x en [%.3f,%.3f]',m,abs(b),X(k),X(k+1))
    % Si b es cero: muestra solo mx
    else
    fprintf('\n%fx \t \t para x en [%.3f,%.3f]',m,X(k),X(k+1))
    end
end
fprintf('\n\n')

% --- PARTE MODIFICADA SOLO PARA MEJORAR EL GRÁFICO ---
figure; % Crea nueva figura
hold on; % Permite superponer elementos
grid on; % Activa la cuadrícula

% Grafica los puntos con mejor estilo
plot(X,Y,'o','MarkerSize',8,'MarkerFaceColor',[0.5 0.5 1],'MarkerEdgeColor','k','LineWidth',1.5)

% Grafica las líneas con mejor estilo
plot(X,Y,'-','Color',[0 0.447 0.741],'LineWidth',2)

% Añade etiquetas profesionales
xlabel('Valores de X','FontSize',11)
ylabel('Valores de Y','FontSize',11)
title('Interpolación Lineal por Partes','FontSize',12)

% Ajusta los márgenes automáticamente
axis tight
% Añade un pequeño margen para mejor visualización
xlim([min(X)-(max(X)-min(X))*0.05, max(X)+(max(X)-min(X))*0.05])
ylim([min(Y)-(max(Y)-min(Y))*0.05, max(Y)+(max(Y)-min(Y))*0.05])