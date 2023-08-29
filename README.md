EXPERIMENT 8
clc; clear all; close all;
N=input('Enter the length of impulse response =');
b=input('Enter the numerator coeff = ');
a=input('Enter the denominator coeff = ');
n=0:N-1;
x=3*ones(1,N);
y=filter(b,a,x)
[h,t]=impz(b,a,N)
[r,p,k]=residuez(b,a)
[H,w]=freqz(b,a,128);
H_mag=abs(H);
figure(1);subplot(3,1,1);stem(n,x);grid;
xlabel('Time index');ylabel ('Amplitude');title('Input sequence'); subplot(3,1,2);stem(n,y);grid;
xlabel('Time index');ylabel('Amplitude');title('System Response'); subplot(3,1,3);stem(t,h);grid;
xlabel('Time index');ylabel('Amplitude');title('Impulse Response'); figure(2);zplane(b,a);grid;
xlabel('Time index');ylabel('Amplitude');title('Z plane');
figure(3); plot(w, H_mag); grid;
xlabel('Time index'); ylabel('Amplitude');title('Frequency Response');
EXPERIMENT 9
clc; clear all; close all;
N=input('Enter the fundamental period of the signal (N)');
M=input('Enter how many points of Fourier series to compute(M=N or M=multiples of N) ') n=0:N-1;
x=[sin(2*pi*n/6)];
for k=0:M-1;
Sum=0;
for n=0:N-1; Ck(k+1)=x(n+1)*exp(-j*2*pi*k*n/N); Sum=Sum+Ck(k+1);
end
Ck(k+1)=Sum/N; end
Mag=abs(Ck);Phase_ang=angle(Ck);
disp(Ck);disp(Mag);disp(Phase_ang); subplot(311);stem([0:length(x)-1],x);xlabel('n-->');ylabel('x(n)');title('Input signal') subplot(312);stem([0:length(Ck)-1],abs(Ck));xlabel('k');ylabel('Magnitude');title('Magnitude Spectrum');
subplot(313);stem([0:length(Ck)-1],Phase_ang); xlabel('k');ylabel('Phase angle');title('Phase Spectrum')
EXPECTED OUTPUT;
For x(n)=sin(2(pi)n/N)
Enter the fundamental period of the signal (N)6
'Enter how many points of Fourier series to compute (M=N or M=multiples of N) 6
M= 6
0.0000 + 0.0000i 0.0000 - 0.5000i -0.0000 + 0.0000i 0.0000 + 0.0000i 0.0000 + 0.0000i 0.0000 + 0.5000i
0.0000 0.5000 0.0000 0.0000 0.0000 0.5000
0 -1.5708 2.9229 1.5075 0.0588 1.5708
For x(n)=cos(2(pi)n/N)
Enter the fundamental period of the signal (N)6
Enter how many points of Fourier series to compute (m>N and m=multiples of N) 6
M= 6
-0.0000 + 0.0000i 0.5000 - 0.0000i -0.0000 + 0.0000i -0.0000 - 0.0000i 0.0000 - 0.0000i 0.5000 + 0.0000i
0.0000 0.5000 0.0000 0.0000 0.0000 0.5000
3.1416 -0.0000 1.7943 -1.9871 -1.1071 0.0000
