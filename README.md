clc; clear all; close all; x=[2 3 6 -3]; n=0:length(x)-1; w=-pi:0.01:pi;
[X] = dtft(x, w);
X_mag=abs(X); X_angle= angle(X); subplot(311);stem(n,x);title('Signal'); xlabel('time index');ylabel('amplitude'); subplot(312);plot(w, X_mag);
title(''Mag. Plot''); xlabel('Frequency w in rad'); ylabel('Mag.');
subplot(313);plot(w, X_angle);
title('Phase plot');xlabel('Frequency w in rad'); ylabel('Phase angle');
