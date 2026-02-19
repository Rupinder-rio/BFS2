# BFS2
clc 
clear all
format short

%phase 1
A=[1 2 1 0;4 5 0 1];
C=[1 1 0 0];
B=[2;20];

%phase 2
n=size(A,2) %4
m=size(A,1) %2

%phase 3
if(n>m)
    ncm=nchoosek(n,m) %6
    pair=nchoosek(1:n,m)
%phase 4 

sol = []
for i = 1:ncm
    y= zeros(n,1);
    x=A(:,pair(i,:))\B;
    if all(x>=0 & x~=inf)
        y(pair(i,:))=x;
        sol = [sol y];
    end
end
end
%phase 5
Z=C*sol;
[zmax,zindex] = max(Z)
Bfs = sol(:,zindex)

%phase 
optimal_value = [Bfs' zmax]
optimal_bfs = array2table(optimal_value)
optimal_bfs.Properties.VariableNames(1:size(optimal_bfs,2)) ={'x1','x2','x3','x4','z'}
