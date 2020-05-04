# kuka_lbr4-_followPath_in_Vrep
The kuka_lbr4+ following one dummy path in CoppeliaSim (Vrep)
the threaded script code:
--reference: http://szmlb.hatenablog.com/entry/2015/01/01/173356
--reference: https://www.youtube.com/watch?v=X73NzCc2E2c
function sysCall_threadmain()
    -- Put some initialization code here
    path = sim.getObjectHandle('Path')
    target = sim.getObjectHandle('target')
    manipVelocity = 0.1
    accel = 0.1
    defaultPosition = sim.getObjectPosition(target, -1)
    defaultOritention = sim.getObjectOrientation(target, -1)
    position = sim.getObjectPosition(target, -1)

    -- Put your main loop here, e.g.:
    --
    -- while sim.getSimulationState()~=sim.simulation_advancing_abouttostop do
    --     local p=sim.getObjectPosition(objHandle,-1)
    --     p[1]=p[1]+0.001
    --     sim.setObjectPosition(objHandle,-1,p)
    --     sim.switchThread() -- resume in next simulation step
    -- end
           
    sim.moveToPosition(target, -1, position, nil, manipVelocity*0.1)
    sim.wait(5)
    sim.followPath(target, path, 3, 0, manipVelocity, accel)
end
